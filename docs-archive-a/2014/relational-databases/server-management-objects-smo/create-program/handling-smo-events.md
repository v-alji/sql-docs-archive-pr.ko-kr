---
title: SMO 이벤트 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- events [SMO]
- SQL Server Management Objects, events
- SMO [SQL Server], events
- events [SMO], about events
ms.assetid: b4f120dd-ba78-46ff-99c5-e47effac8544
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7ea438142ac283c5ad19670fa827b5e248e80f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660458"
---
# <a name="handling-smo-events"></a><span data-ttu-id="666a1-102">SMO 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="666a1-102">Handling SMO Events</span></span>
  <span data-ttu-id="666a1-103">이벤트 처리기 및 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용하여 구독할 수 있는 서버 이벤트 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-103">There are server event types that can be subscribed to by using an event handler and the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
 <span data-ttu-id="666a1-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects(SMO)의 인스턴스 클래스 대부분은 서버에서 특정 동작이 발생할 때 이벤트를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-104">Many of the instance classes in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) can trigger events when certain actions on the server occur.</span></span>  
  
 <span data-ttu-id="666a1-105">이러한 이벤트는 이벤트 처리기를 설정하고 연관된 이벤트를 구독하여 프로그래밍 방식으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-105">These events can be handled programmatically by setting up an event handler and subscribing to the associated events.</span></span> <span data-ttu-id="666a1-106">모든 구독은 SMO 클라이언트 프로그램이 종료될 때 제거되므로 이런 유형의 이벤트 처리는 일시적입니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-106">This type of event handling is transient because all the subscriptions are removed when the SMO client program exits.</span></span>  
  
## <a name="connectioncontext-event-handling"></a><span data-ttu-id="666a1-107">ConnectionContext 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="666a1-107">ConnectionContext Event Handling</span></span>  
 <span data-ttu-id="666a1-108"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체는 여러 이벤트 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-108">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object supports several event types.</span></span> <span data-ttu-id="666a1-109">이벤트 속성을 적절한 이벤트 처리기 인스턴스로 설정한 다음, 이벤트 처리기 개체를 이벤트를 처리하는 보호된 함수로 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-109">The event property must be set to an instance of an appropriate event handler, and the event handler object must be defined as a protected function that handles the event.</span></span>  
  
## <a name="event-subscription"></a><span data-ttu-id="666a1-110">이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="666a1-110">Event Subscription</span></span>  
 <span data-ttu-id="666a1-111">이벤트 처리기 클래스를 작성하고, 해당 인스턴스를 만들고, 이벤트 처리기를 부모 개체에 할당하고, 이벤트를 구독하는 방법으로 이벤트를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-111">You handle events by writing an event handler class, creating an instance of it, assigning the event handler to the parent object, and then subscribing to the event.</span></span>  
  
 <span data-ttu-id="666a1-112">이벤트를 처리하려면 이벤트 처리기 클래스를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-112">An event handler class must be written to handle events.</span></span> <span data-ttu-id="666a1-113">이벤트 처리기 클래스는 여러 개의 이벤트 처리기 함수를 포함할 수 있고, 이벤트를 처리하려면 이 클래스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-113">The event handler class can contain more than one event handler function, and must be installed for the events to be handled.</span></span> <span data-ttu-id="666a1-114">이벤트 처리기 함수는 이벤트에 대 한 정보를 보고 하는 데 사용할 수 있는 이벤트에 대 한 정보를 *ServerEventNotificatificationArgs* 매개 변수에서 받습니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-114">The event handler functions receive information about the event from the *ServerEventNotificatificationArgs* parameter that can be used to report information about the event.</span></span>  
  
 <span data-ttu-id="666a1-115">처리할 수 있는 데이터베이스 및 서버 이벤트의 유형은 클래스 및 클래스에 나열 됩니다 <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet> .</span><span class="sxs-lookup"><span data-stu-id="666a1-115">The types of database and server events that can be handled are listed in the <xref:Microsoft.SqlServer.Management.Smo.DatabaseEventSet> class and the <xref:Microsoft.SqlServer.Management.Smo.ServerEventSet>class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="666a1-116">예제</span><span class="sxs-lookup"><span data-stu-id="666a1-116">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-basic"></a><span data-ttu-id="666a1-117">Visual Basic에서 이벤트 처리기 등록 및 이벤트 처리 구독</span><span class="sxs-lookup"><span data-stu-id="666a1-117">Registering Event Handlers and Subscribing to Event Handling in Visual Basic</span></span>  
 <span data-ttu-id="666a1-118">이 코드 예제는 이벤트 처리기를 설정하는 방법과 데이터베이스 이벤트를 구독하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-118">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEvents1](SMO How to#SMO_VBEvents1)]  -->  
  
## <a name="registering-event-handlers-and-subscribing-to-event-handling-in-visual-c"></a><span data-ttu-id="666a1-119">Visual C#에서 이벤트 처리기 등록 및 이벤트 처리 구독</span><span class="sxs-lookup"><span data-stu-id="666a1-119">Registering Event Handlers and Subscribing to Event Handling in Visual C#</span></span>  
 <span data-ttu-id="666a1-120">이 코드 예제는 이벤트 처리기를 설정하는 방법과 데이터베이스 이벤트를 구독하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="666a1-120">This code example shows how to set up the event handler, and how to subscribe to the database events.</span></span>  
  
```  
//Create an event handler subroutine that runs when a table is created.   
private void MyCreateEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been added to the AdventureWorks2012 database.");   
}   
//Create an event handler subroutine that runs when a table is deleted.   
private void MyDropEventHandler(object sender, ServerEventArgs e)   
{   
Console.WriteLine("A table has just been dropped from the AdventureWorks2012 database.");   
}   
public void Main()   
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Create a database event set that contains the CreateTable event only.   
DatabaseEventSet databaseCreateEventSet = new DatabaseEventSet();   
databaseCreateEventSet.CreateTable = true;   
//Create a server event handler and set it to the first event handler subroutine.   
ServerEventHandler serverCreateEventHandler;   
serverCreateEventHandler = new ServerEventHandler(MyCreateEventHandler);   
//Subscribe to the first server event handler when a CreateTable event occurs.   
db.Events.SubscribeToEvents(databaseCreateEventSet, serverCreateEventHandler);   
    //Create a database event set that contains the DropTable event only.   
DatabaseEventSet databaseDropEventSet = new DatabaseEventSet();   
databaseDropEventSet.DropTable = true;   
//Create a server event handler and set it to the second event handler subroutine.   
ServerEventHandler serverDropEventHandler;   
serverDropEventHandler = new ServerEventHandler(MyDropEventHandler);   
//Subscribe to the second server event handler when a DropTable event occurs.   
db.Events.SubscribeToEvents(databaseDropEventSet, serverDropEventHandler);   
//Start event handling.   
db.Events.StartEvents();   
//Create a table on the database.   
Table tb;   
tb = new Table(db, "Test_Table");   
Column mycol1;   
mycol1 = new Column(tb, "Name", DataType.NChar(50));   
mycol1.Collation = "Latin1_General_CI_AS";   
mycol1.Nullable = true;   
tb.Columns.Add(mycol1);   
tb.Create();   
//Remove the table.   
tb.Drop();   
//Wait until the events have occured.   
int x;   
int y;   
for (x = 1; x <= 1000000000; x++) {   
    y = x * 2;   
}   
//Stop event handling.   
db.Events.StopEvents();   
}  
```  
  
  
