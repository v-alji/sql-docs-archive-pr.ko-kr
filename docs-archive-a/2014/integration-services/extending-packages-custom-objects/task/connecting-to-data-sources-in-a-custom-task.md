---
title: 사용자 지정 태스크에서 데이터 원본에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ConnectionManager objects
- connection managers [Integration Services], external data sources
- data sources [Integration Services], external
- custom tasks [Integration Services], external data sources
- external data sources [Integration Services]
- connections [Integration Services], external data sources
- SSIS custom tasks, external data sources
ms.assetid: 9f0b3a43-3eaa-4b3c-bb08-29b630c11306
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71c504f4b528a0c9809d00de74de4beb9c67c4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652222"
---
# <a name="connecting-to-data-sources-in-a-custom-task"></a><span data-ttu-id="8398e-102">사용자 지정 태스크에서 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="8398e-102">Connecting to Data Sources in a Custom Task</span></span>
  <span data-ttu-id="8398e-103">태스크는 연결 관리자를 통해 외부 데이터 원본에 연결하여 데이터를 검색하거나 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-103">Tasks connect to external data sources to retrieve or save data by using a connection manager.</span></span> <span data-ttu-id="8398e-104">디자인 타임에 연결 관리자는 논리적 연결을 나타내며 서버 이름 및 인증 속성과 같은 주요 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-104">At design time, a connection manager represents a logical connection, and describes key information such as the server name and any authentication properties.</span></span> <span data-ttu-id="8398e-105">런타임에 태스크에서는 연결 관리자의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하여 데이터 원본에 대한 실제 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-105">At run time, tasks call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of the connection manager to establish the physical connection to the data source.</span></span>  
  
 <span data-ttu-id="8398e-106">패키지에는 각기 다른 데이터 원본에 연결하는 여러 태스크가 있을 수 있으므로 패키지에서는 모든 연결 관리자를 <xref:Microsoft.SqlServer.Dts.Runtime.Connections>라는 컬렉션에서 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-106">Because a package can contain many tasks, each of which may have connections to different data sources, the package tracks all the connection managers in a collection, the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection.</span></span> <span data-ttu-id="8398e-107">태스크에서는 해당 패키지의 컬렉션을 사용하여 유효성 검사 및 실행 중 사용할 연결 관리자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-107">Tasks use the collection in their package to find the connection manager that they will use during validation and execution.</span></span> <span data-ttu-id="8398e-108"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> 컬렉션은 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드에 대한 첫 번째 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-108">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection is the first parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
 <span data-ttu-id="8398e-109">컬렉션의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체를 사용자에게 표시하거나 그래픽 사용자 인터페이스의 대화 상자 또는 드롭다운 목록을 사용하여 태스크에서 잘못된 연결 관리자를 사용하지 못하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-109">You can prevent the task from using the wrong connection manager by displaying the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects from the collection to the user, by using a dialog box or drop-down list in the graphical user interface.</span></span> <span data-ttu-id="8398e-110">이렇게 하면 사용자는 패키지에 포함된 적절한 유형의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체 중에서만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-110">This gives the user a way to select from among only those <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects of the appropriate type that are contained in the package.</span></span>  
  
 <span data-ttu-id="8398e-111">태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하여 데이터 원본에 대한 실제 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-111">Tasks call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the physical connection to the data source.</span></span> <span data-ttu-id="8398e-112">이 메서드는 태스크에서 사용될 수 있는 기본 연결 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-112">The method returns the underlying connection object that can then be used by the task.</span></span> <span data-ttu-id="8398e-113">연결 관리자는 기본 연결 개체의 구현 세부 사항을 태스크에서 격리하므로 태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 호출하여 연결을 설정하기만 하면 되고 연결의 다른 측면은 고려할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-113">Because the connection manager isolates the implementation details of the underlying connection object from the task, the task only has to call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the connection, and does not have to be concerned with other aspects of the connection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8398e-114">예제</span><span class="sxs-lookup"><span data-stu-id="8398e-114">Example</span></span>  
 <span data-ttu-id="8398e-115">다음 예제 코드에서는 Validate 및 Execute 메서드에서 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 이름의 유효성을 검사하는 방법과 Execute 메서드에서 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 메서드를 사용하여 실제 연결을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8398e-115">The following sample code demonstrates validation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> name in the Validate and Execute methods, and shows how to use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the physical connection in the Execute method.</span></span>  
  
```csharp  
private string connectionManagerName = "";  
  
public string ConnectionManagerName  
{  
  get { return this.connectionManagerName; }  
  set { this.connectionManagerName = value; }  
}  
  
public override DTSExecResult Validate(  
  Connections connections, VariableDispenser variableDispenser,  
  IDTSComponentEvents componentEvents, IDTSLogging log)  
{  
  // If the connection manager exists, validation is successful;  
  // otherwise, fail validation.  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception e)  
  {  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
  
public override DTSExecResult Execute(Connections connections,   
  VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,   
  IDTSLogging log, object transaction)  
{  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    object connection = cm.AcquireConnection(transaction);  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception exception)  
  {  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
```  
  
```vb  
Private _connectionManagerName As String = ""  
  
Public Property ConnectionManagerName() As String  
  Get  
    Return Me._connectionManagerName  
  End Get  
  Set(ByVal Value As String)  
    Me._connectionManagerName = value  
  End Set  
End Property  
  
Public Overrides Function Validate( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  ' If the connection manager exists, validation is successful;  
  ' otherwise fail validation.  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Return DTSExecResult.Success  
  Catch e As System.Exception  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
  
Public Overrides Function Execute( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging, ByVal transaction As Object) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Dim connection As Object = cm.AcquireConnection(transaction)  
    Return DTSExecResult.Success  
  Catch exception As System.Exception  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
```  
  
<span data-ttu-id="8398e-116">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="8398e-116">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="8398e-117">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="8398e-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="8398e-118">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="8398e-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="8398e-119">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="8398e-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8398e-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8398e-120">See Also</span></span>  
 <span data-ttu-id="8398e-121">[SSIS&#41; 연결을 &#40;Integration Services](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="8398e-121">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="8398e-122">연결 관리자 만들기</span><span class="sxs-lookup"><span data-stu-id="8398e-122">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
