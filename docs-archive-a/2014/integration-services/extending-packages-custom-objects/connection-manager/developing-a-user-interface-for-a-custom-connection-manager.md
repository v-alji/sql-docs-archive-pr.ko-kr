---
title: 사용자 지정 연결 관리자의 사용자 인터페이스 개발 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], developing user interface
- custom user interface [Integration Services], custom connection manager
ms.assetid: 908bf2ac-fc84-4af8-a869-1cb43573d2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc0e9f2a76f3d97c925c44219683ca6cd655e43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650192"
---
# <a name="developing-a-user-interface-for-a-custom-connection-manager"></a><span data-ttu-id="880d7-102">사용자 지정 연결 관리자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="880d7-102">Developing a User Interface for a Custom Connection Manager</span></span>
  <span data-ttu-id="880d7-103">기본 클래스의 속성 및 메서드 구현을 재정의하여 사용자 지정 기능을 제공한 후 연결 관리자의 사용자 지정 사용자 인터페이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your connection manager.</span></span> <span data-ttu-id="880d7-104">사용자 지정 사용자 인터페이스를 만들지 않은 경우 사용자는 속성 창에서만 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-104">If you do not create a custom user interface, users can configure your connection manager only by using the Properties window.</span></span>  
  
 <span data-ttu-id="880d7-105">사용자 지정 사용자 인터페이스 프로젝트 또는 어셈블리에는 일반적으로 두 개의 클래스가 포함됩니다. 하나는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>를 구현하는 클래스이고 다른 하나는 이 클래스에서 사용자로부터 정보를 수집하기 위해 표시하는 Windows Form입니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-105">In a custom user interface project or assembly, you normally have two classes-a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>, and the Windows form that it displays to gather information from the user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="880d7-106">[사용자 지정 연결 관리자 코딩](../building-deploying-and-debugging-custom-objects.md)에 설명된 대로 사용자 지정 사용자 인터페이스를 서명 및 빌드하고 전역 어셈블리 캐시에 설치한 후에는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> 속성에서 이 클래스의 정규화된 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-106">After signing and building your custom user interface and installing it in the global assembly cache as described in [Coding a Custom Connection Manager](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="880d7-107">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 기본 제공된 대부분의 태스크, 원본 및 대상은 특정 유형의 기본 제공 연결 관리자와만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="880d7-108">따라서 이러한 예제를 기본 제공 태스크 및 구성 요소와 함께 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-108">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="coding-the-user-interface-class"></a><span data-ttu-id="880d7-109">사용자 인터페이스 클래스 코딩</span><span class="sxs-lookup"><span data-stu-id="880d7-109">Coding the User Interface Class</span></span>  
 <span data-ttu-id="880d7-110"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 인터페이스에는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> 등의 메서드 네 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-110">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface has four methods: <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A>.</span></span> <span data-ttu-id="880d7-111">다음 섹션에서는 이 네 개의 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-111">The following sections describe these four methods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="880d7-112">사용자가 연결 관리자의 인스턴스를 삭제할 때 정리 작업을 수행할 필요가 없으면 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> 메서드에 대한 코드를 작성하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-112">You may not need to write any code for the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> method if no cleanup is required when the user deletes an instance of the connection manager.</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="880d7-113">사용자 인터페이스 초기화</span><span class="sxs-lookup"><span data-stu-id="880d7-113">Initializing the User Interface</span></span>  
 <span data-ttu-id="880d7-114"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> 메서드에서 디자이너는 사용자 인터페이스 클래스에서 연결 관리자의 속성을 수정할 수 있도록 구성할 연결 관리자에 대한 참조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-114">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> method, the designer provides a reference to the connection manager that is being configured so that the user interface class can modify the connection manager's properties.</span></span> <span data-ttu-id="880d7-115">다음 코드에서 보여 주는 것과 같이 코드에서는 나중에 사용할 수 있도록 연결 관리자에 대한 참조를 캐시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-115">As shown in the following code, your code needs to cache the reference to the connection managerfor later use.</span></span>  
  
```vb  
Public Sub Initialize(ByVal connectionManager As Microsoft.SqlServer.Dts.Runtime.ConnectionManager, ByVal serviceProvider As System.IServiceProvider) Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize  
  
    _connectionManager = connectionManager  
    _serviceProvider = serviceProvider  
  
  End Sub  
```  
  
```csharp  
public void Initialize(Microsoft.SqlServer.Dts.Runtime.ConnectionManager connectionManager, System.IServiceProvider serviceProvider)  
{  
  
  _connectionManager = connectionManager;  
  _serviceProvider = serviceProvider;  
  
}  
```  
  
### <a name="creating-a-new-instance-of-the-user-interface"></a><span data-ttu-id="880d7-116">사용자 인터페이스의 새 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="880d7-116">Creating a New Instance of the User Interface</span></span>  
 <span data-ttu-id="880d7-117">생성자가 아닌 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> 메서드는 사용자가 연결 관리자의 새 인스턴스를 만들 때 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> 메서드 다음에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-117">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> method, which is not a constructor, is called after the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> method when the user creates a new instance of the connection manager.</span></span> <span data-ttu-id="880d7-118">사용자가 기존 연결 관리자를 복사하여 붙여 넣지 않은 경우 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> 메서드에서는 일반적으로 편집용 폼을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-118">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> method, you usually want to display the form for editing, unless the user has copied and pasted an existing connection manager.</span></span> <span data-ttu-id="880d7-119">다음 코드에서는 이 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-119">The following code shows an implementation of this method.</span></span>  
  
```vb  
Public Function [New](ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, ByVal connectionUIArgs As Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs) As Boolean Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New  
  
  Dim clipboardService As IDtsClipboardService  
  
  clipboardService = _  
    DirectCast(_serviceProvider.GetService(GetType(IDtsClipboardService)), IDtsClipboardService)  
  If Not clipboardService Is Nothing Then  
    ' If the connection manager has been copied and pasted, take no action.  
    If clipboardService.IsPasteActive Then  
      Return True  
    End If  
  End If  
  
  Return EditSqlConnection(parentWindow)  
  
End Function  
```  
  
```csharp  
public bool New(System.Windows.Forms.IWin32Window parentWindow, Microsoft.SqlServer.Dts.Runtime.Connections connections, Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs connectionUIArgs)  
  {  
    IDtsClipboardService clipboardService;  
  
    clipboardService = (IDtsClipboardService)_serviceProvider.GetService(typeof(IDtsClipboardService));  
    if (clipboardService != null)  
    // If connection manager has been copied and pasted, take no action.  
    {  
      if (clipboardService.IsPasteActive)  
      {  
        return true;  
      }  
    }  
  
    return EditSqlConnection(parentWindow);  
  }  
```  
  
### <a name="editing-the-connection-manager"></a><span data-ttu-id="880d7-120">연결 관리자 편집</span><span class="sxs-lookup"><span data-stu-id="880d7-120">Editing the Connection Manager</span></span>  
 <span data-ttu-id="880d7-121">편집용 폼은 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 메서드 모두에서 호출되므로 도우미 함수를 사용하여 폼을 표시하는 코드를 캡슐화하는 것이 편리합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-121">Because the form for editing is called from both the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> methods, it is convenient to use a helper function to encapsulate the code that displays the form.</span></span> <span data-ttu-id="880d7-122">다음 코드에서는 이 도우미 함수의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-122">The following code shows an implementation of this helper function.</span></span>  
  
```vb  
Private Function EditSqlConnection(ByVal parentWindow As IWin32Window) As Boolean  
  
  Dim sqlCMUIForm As New SqlConnMgrUIFormVB  
  
  sqlCMUIForm.Initialize(_connectionManager, _serviceProvider)  
  If sqlCMUIForm.ShowDialog(parentWindow) = DialogResult.OK Then  
    Return True  
  Else  
    Return False  
  End If  
  
End Function  
```  
  
```csharp  
private bool EditSqlConnection(IWin32Window parentWindow)  
 {  
  
   SqlConnMgrUIFormCS sqlCMUIForm = new SqlConnMgrUIFormCS();  
  
   sqlCMUIForm.Initialize(_connectionManager, _serviceProvider);  
   if (sqlCMUIForm.ShowDialog(parentWindow) == DialogResult.OK)  
   {  
     return true;  
   }  
   else  
   {  
     return false;  
   }  
  
 }  
```  
  
 <span data-ttu-id="880d7-123"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 메서드에서는 편집용 폼을 표시하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-123">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> method, you simply have to display the form for editing.</span></span> <span data-ttu-id="880d7-124">다음 코드에서는 도우미 함수를 사용하여 폼의 코드를 캡슐화하는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-124">The following code shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> method that uses a helper function to encapsulate the code for the form.</span></span>  
  
```vb  
Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, ByVal connectionUIArg As Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs) As Boolean Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit  
  
  Return EditSqlConnection(parentWindow)  
  
End Function  
```  
  
```csharp  
public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Microsoft.SqlServer.Dts.Runtime.Connections connections, Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs connectionUIArg)  
{  
  
  return EditSqlConnection(parentWindow);  
  
}  
```  
  
## <a name="coding-the-user-interface-form"></a><span data-ttu-id="880d7-125">사용자 인터페이스 폼 코딩</span><span class="sxs-lookup"><span data-stu-id="880d7-125">Coding the User Interface Form</span></span>  
 <span data-ttu-id="880d7-126"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 인터페이스의 메서드를 구현하는 사용자 인터페이스 클래스를 만든 후에는 사용자가 연결 관리자의 속성을 구성할 수 있는 Windows Form을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-126">After creating the user interface class that implements the methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface, you must create a Windows form where the user can configure the properties of your connection manager.</span></span>  
  
### <a name="initializing-the-user-interface-form"></a><span data-ttu-id="880d7-127">사용자 인터페이스 폼 초기화</span><span class="sxs-lookup"><span data-stu-id="880d7-127">Initializing the User Interface Form</span></span>  
 <span data-ttu-id="880d7-128">편집용 사용자 지정 폼을 표시하면 편집할 연결 관리자에 대한 참조를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-128">When you display your custom form for editing, you can pass a reference to the connection manager that is being edited.</span></span> <span data-ttu-id="880d7-129">폼 클래스의 사용자 지정 생성자를 사용하거나 여기에 표시된 대로 `Initialize` 메서드를 만들어 이 참조를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-129">You can pass this reference either by using a custom constructor for the form class, or by creating your own `Initialize` method as shown here.</span></span>  
  
```vb  
Public Sub Initialize(ByVal connectionManager As ConnectionManager, ByVal serviceProvider As IServiceProvider)  
  
  _connectionManager = connectionManager  
  _serviceProvider = serviceProvider  
  ConfigureControlsFromConnectionManager()  
  EnableControls()  
  
End Sub  
```  
  
```csharp  
public void Initialize(ConnectionManager connectionManager, IServiceProvider serviceProvider)  
 {  
  
   _connectionManager = connectionManager;  
   _serviceProvider = serviceProvider;  
   ConfigureControlsFromConnectionManager();  
   EnableControls();  
  
 }  
```  
  
### <a name="setting-properties-on-the-user-interface-form"></a><span data-ttu-id="880d7-130">사용자 인터페이스 폼의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="880d7-130">Setting Properties on the User Interface Form</span></span>  
 <span data-ttu-id="880d7-131">마지막으로 폼 클래스에는 해당 폼이 처음 로드될 때 폼의 컨트롤을 연결 관리자의 기존 또는 기본 속성 값으로 채우는 도우미 함수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-131">Finally, your form class needs a helper function that populates the controls on the form when it is first loaded with the existing or the default values of the properties of the connection manager.</span></span> <span data-ttu-id="880d7-132">또한 폼 클래스에는 사용자가 "확인"을 클릭하고 폼을 닫을 때 속성 값을 사용자가 입력한 값으로 설정하는 유사한 함수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="880d7-132">Your form class also needs a similar function that sets the values of the properties to the values entered by the user when the user clicks OK and closes the form.</span></span>  
  
```vb  
Private Const CONNECTIONNAME_BASE As String = "SqlConnectionManager"  
  
Private Sub ConfigureControlsFromConnectionManager()  
  
  Dim tempName As String  
  Dim tempServerName As String  
  Dim tempDatabaseName As String  
  
  With _connectionManager  
  
    tempName = .Properties("Name").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempName) Then  
      _connectionName = tempName  
    Else  
      _connectionName = CONNECTIONNAME_BASE  
    End If  
  
    tempServerName = .Properties("ServerName").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempServerName) Then  
      _serverName = tempServerName  
      txtServerName.Text = _serverName  
    End If  
  
    tempDatabaseName = .Properties("DatabaseName").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempDatabaseName) Then  
      _databaseName = tempDatabaseName  
      txtDatabaseName.Text = _databaseName  
    End If  
  
  End With  
  
End Sub  
  
Private Sub ConfigureConnectionManagerFromControls()  
  
  With _connectionManager  
    .Properties("Name").SetValue(_connectionManager, _connectionName)  
    .Properties("ServerName").SetValue(_connectionManager, _serverName)  
    .Properties("DatabaseName").SetValue(_connectionManager, _databaseName)  
  End With  
  
End Sub  
```  
  
```csharp  
private const string CONNECTIONNAME_BASE = "SqlConnectionManager";  
  
private void ConfigureControlsFromConnectionManager()  
 {  
  
   string tempName;  
   string tempServerName;  
   string tempDatabaseName;  
  
   {  
     tempName = _connectionManager.Properties["Name"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempName))  
     {  
       _connectionName = tempName;  
     }  
     else  
     {  
       _connectionName = CONNECTIONNAME_BASE;  
     }  
  
     tempServerName = _connectionManager.Properties["ServerName"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempServerName))  
     {  
       _serverName = tempServerName;  
       txtServerName.Text = _serverName;  
     }  
  
     tempDatabaseName = _connectionManager.Properties["DatabaseName"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempDatabaseName))  
     {  
       _databaseName = tempDatabaseName;  
       txtDatabaseName.Text = _databaseName;  
     }  
  
   }  
  
 }  
  
 private void ConfigureConnectionManagerFromControls()  
 {  
  
   {  
     _connectionManager.Properties["Name"].SetValue(_connectionManager, _connectionName);  
     _connectionManager.Properties["ServerName"].SetValue(_connectionManager, _serverName);  
     _connectionManager.Properties["DatabaseName"].SetValue(_connectionManager, _databaseName);  
   }  
  
 }  
```  
  
<span data-ttu-id="880d7-133">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="880d7-133">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="880d7-134">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="880d7-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="880d7-135">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="880d7-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="880d7-136">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="880d7-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880d7-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="880d7-137">See Also</span></span>  
 <span data-ttu-id="880d7-138">[사용자 지정 연결 관리자 만들기](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="880d7-138">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="880d7-139">사용자 지정 연결 관리자 코딩</span><span class="sxs-lookup"><span data-stu-id="880d7-139">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
  
  
