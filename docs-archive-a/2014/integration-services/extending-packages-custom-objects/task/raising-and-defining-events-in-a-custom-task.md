---
title: 사용자 지정 태스크에서 이벤트 발생 및 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS events, custom
- status information [SQL Server], task events
- custom tasks [Integration Services], events
- SSIS custom tasks, events
- IDTSComponentEvents interface
- events [Integration Services], custom
- events [Integration Services], runtime
- custom events [Integration Services]
- SSIS events, runtime
- IDTSEvents interface
ms.assetid: e0898aa1-e90c-4c4e-99d4-708a76efddfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb41ee60543a05b6cf10b3acda43372e20288d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652953"
---
# <a name="raising-and-defining-events-in-a-custom-task"></a><span data-ttu-id="c7ad9-102">사용자 지정 태스크에서 이벤트 발생 및 정의</span><span class="sxs-lookup"><span data-stu-id="c7ad9-102">Raising and Defining Events in a Custom Task</span></span>
  <span data-ttu-id="c7ad9-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임 엔진에서는 태스크의 유효성 검사 및 실행 시 태스크의 진행 상태에 대한 정보를 제공하는 이벤트의 컬렉션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine provides a collection of events that provide status on the progress of a task as the task is validated and executed.</span></span> <span data-ttu-id="c7ad9-104"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 인터페이스는 이러한 이벤트를 정의하며 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> 메서드에 대한 매개 변수로 태스크에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-104">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface defines these events, and is provided to tasks as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> methods.</span></span>  
  
 <span data-ttu-id="c7ad9-105"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 인터페이스에 정의되며 태스크 대신 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서 발생시키는 다른 이벤트 집합도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-105">There is another set of events, which are defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface, that are raised on behalf of the task by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="c7ad9-106"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서는 유효성 검사 및 실행 전후에 이벤트를 발생시키는 반면 태스크에서는 실행 및 유효성 검사 도중에 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-106">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> raises events that occur before and after validation and execution, whereas the task raises the events that occur during execution and validation.</span></span>  
  
## <a name="creating-custom-events"></a><span data-ttu-id="c7ad9-107">사용자 지정 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="c7ad9-107">Creating Custom Events</span></span>  
 <span data-ttu-id="c7ad9-108">사용자 지정 태스크 개발자는 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> 메서드의 재정의된 구현에서 새 <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A>를 만들어 새 사용자 지정 이벤트를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-108">Custom task developers can define new, custom events by creating a new <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> in their overridden implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A> method.</span></span> <span data-ttu-id="c7ad9-109">만들어진 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo>는 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> 메서드를 사용하여 `EventInfos` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-109">After the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> is created, it is added to the `EventInfos` collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> method.</span></span> <span data-ttu-id="c7ad9-110"><xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> 메서드의 서명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-110">The method signature of the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> method is as follows:</span></span>  
  
 `public void Add(string eventName, string description, bool allowEventHandlers, string[] parameterNames, TypeCode[] parameterTypes, string[] parameterDescriptions);`  
  
 <span data-ttu-id="c7ad9-111">다음 코드 예제에서는 두 개의 사용자 지정 이벤트를 만들고 해당 속성을 설정하는 사용자 지정 태스크의 `InitializeTask` 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-111">The following code sample shows the `InitializeTask` method of a custom task, where two custom events are created and their properties are set.</span></span> <span data-ttu-id="c7ad9-112">그런 다음 새 이벤트를 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-112">The new events are then added to the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> collection.</span></span>  
  
 <span data-ttu-id="c7ad9-113">첫 번째 사용자 지정 이벤트에는 "**OnBeforeIncrement**"라는 *eventName*과 "**Fires after the initial value is updated.**"라는 *description*이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-113">The first custom event has an *eventName* of "**OnBeforeIncrement**" and *description* of "**Fires after the initial value is updated.**"</span></span> <span data-ttu-id="c7ad9-114">다음 매개 변수인 `true` 값은 이 이벤트에서 이벤트를 처리하기 위한 이벤트 처리기 컨테이너가 만들어지는 것을 허용해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-114">The next parameter, the `true` value, indicates that this event should allow an event handler container to be created to handle the event.</span></span> <span data-ttu-id="c7ad9-115">이벤트 처리기는 패키지, 시퀀스, ForLoop, ForEachLoop 등의 다른 컨테이너와 같이 태스크에 패키지의 구조와 서비스를 제공하는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-115">The event handler is a container that provides structure in a package and services to tasks, like other containers such as the package, Sequence, ForLoop, and ForEachLoop.</span></span> <span data-ttu-id="c7ad9-116">*AllowEventHandlers* 매개 변수가 이면 `true` <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 이벤트에 대 한 개체가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-116">When the *allowEventHandlers* parameter is `true`, <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects are created for the event.</span></span> <span data-ttu-id="c7ad9-117">그러면 해당 이벤트에 대해 정의된 모든 매개 변수를 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>의 변수 컬렉션에 있는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-117">Any parameters that were defined for the event are now available to the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> in the variables collection of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.</span></span>  
  
```csharp  
public override void InitializeTask(Connections connections,  
   VariableDispenser variables, IDTSInfoEvents events,  
   IDTSLogging log, EventInfos eventInfos,  
   LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
{  
    this.eventInfos = eventInfos;  
    string[] paramNames = new string[1];  
    TypeCode[] paramTypes = new TypeCode[1]{TypeCode.Int32};  
    string[] paramDescriptions = new string[1];  
  
    paramNames[0] = "InitialValue";  
    paramDescriptions[0] = "The value before it is incremented.";  
  
    this.eventInfos.Add("OnBeforeIncrement",   
      "Fires before the task increments the value.",  
      true,paramNames,paramTypes,paramDescriptions);  
    this.onBeforeIncrement = this.eventInfos["OnBeforeIncrement"];  
  
    paramDescriptions[0] = "The value after it has been incremented.";  
    this.eventInfos.Add("OnAfterIncrement",  
      "Fires after the initial value is updated.",  
      true,paramNames, paramTypes,paramDescriptions);  
    this.onAfterIncrement = this.eventInfos["OnAfterIncrement"];  
}  
```  
  
```vb  
Public Overrides Sub InitializeTask(ByVal connections As Connections, _  
ByVal variables As VariableDispenser, ByVal events As IDTSInfoEvents, _  
ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, _  
ByVal logEntryInfos As LogEntryInfos, ByVal refTracker As ObjectReferenceTracker)   
  
    Dim paramNames(0) As String  
    Dim paramTypes(0) As TypeCode = {TypeCode.Int32}  
    Dim paramDescriptions(0) As String  
  
    Me.eventInfos = eventInfos  
  
    paramNames(0) = "InitialValue"  
    paramDescriptions(0) = "The value before it is incremented."  
  
    Me.eventInfos.Add("OnBeforeIncrement", _  
      "Fires before the task increments the value.", _  
      True, paramNames, paramTypes, paramDescriptions)  
    Me.onBeforeIncrement = Me.eventInfos("OnBeforeIncrement")  
  
    paramDescriptions(0) = "The value after it has been incremented."  
    Me.eventInfos.Add("OnAfterIncrement", _  
      "Fires after the initial value is updated.", True, _  
      paramNames, paramTypes, paramDescriptions)  
    Me.onAfterIncrement = Me.eventInfos("OnAfterIncrement")  
  
End Sub  
```  
  
## <a name="raising-custom-events"></a><span data-ttu-id="c7ad9-118">사용자 지정 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="c7ad9-118">Raising Custom Events</span></span>  
 <span data-ttu-id="c7ad9-119">사용자 지정 이벤트는 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> 메서드를 호출하면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-119">Custom events are raised by calling the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="c7ad9-120">다음 코드 줄은 사용자 지정 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-120">The following line of code raises a custom event.</span></span>  
  
```csharp  
componentEvents.FireCustomEvent(this.onBeforeIncrement.Name,  
   this.onBeforeIncrement.Description, ref arguments,  
   null, ref bFireOnBeforeIncrement);  
```  
  
```vb  
componentEvents.FireCustomEvent(Me.onBeforeIncrement.Name, _  
Me.onBeforeIncrement.Description, arguments, _  
Nothing,  bFireOnBeforeIncrement)  
```  
  
## <a name="sample"></a><span data-ttu-id="c7ad9-121">샘플</span><span class="sxs-lookup"><span data-stu-id="c7ad9-121">Sample</span></span>  
 <span data-ttu-id="c7ad9-122">다음 예에서는 `InitializeTask` 메서드에서 사용자 지정 이벤트를 정의하고 이 사용자 지정 이벤트를 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> 컬렉션에 추가한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> 메서드를 호출하여 `Execute` 메서드 실행 중 사용자 지정 이벤트를 발생시키는 태스크를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-122">The following example shows a task that defines a custom event in the `InitializeTask` method, adds the custom event to the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> collection, and then raises the custom event during its `Execute` method by calling the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> method.</span></span>  
  
```csharp  
[DtsTask(DisplayName = "CustomEventTask")]  
    public class CustomEventTask : Task  
    {  
        public override DTSExecResult Execute(Connections connections,   
          VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,  
           IDTSLogging log, object transaction)  
        {  
            bool fireAgain;  
            object[] args = new object[1] { "The value of the parameter." };  
            componentEvents.FireCustomEvent( "MyCustomEvent",   
              "Firing the custom event.", ref args,  
              "CustomEventTask" , ref fireAgain );  
            return DTSExecResult.Success;  
        }  
  
        public override void InitializeTask(Connections connections,  
          VariableDispenser variableDispenser, IDTSInfoEvents events,  
          IDTSLogging log, EventInfos eventInfos,  
          LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
        {  
            string[] names = new string[1] {"Parameter1"};  
            TypeCode[] types = new TypeCode[1] {TypeCode.String};  
            string[] descriptions = new string[1] {"Parameter description." };  
  
            eventInfos.Add("MyCustomEvent",  
             "Fires when my interesting event happens.",  
             true, names, types, descriptions);  
  
        }  
   }  
```  
  
```vb  
<DtsTask(DisplayName = "CustomEventTask")> _   
    Public Class CustomEventTask  
     Inherits Task  
        Public Overrides Function Execute(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser, _  
          ByVal componentEvents As IDTSComponentEvents, _  
          ByVal log As IDTSLogging, ByVal transaction As Object) _  
          As DTSExecResult  
  
            Dim fireAgain As Boolean  
            Dim args() As Object =  New Object(1) {"The value of the parameter."}  
  
            componentEvents.FireCustomEvent("MyCustomEvent", _  
              "Firing the custom event.", args, _  
              "CustomEventTask" ,  fireAgain)  
            Return DTSExecResult.Success  
        End Function  
  
        Public Overrides  Sub InitializeTask(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser,  
          ByVal events As IDTSInfoEvents,  
          ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, ByVal logEnTryInfos As LogEnTryInfos, ByVal refTracker As ObjectReferenceTracker)  
  
            Dim names() As String =  New String(1) {"Parameter1"}  
            Dim types() As TypeCode =  New TypeCode(1) {TypeCode.String}  
            Dim descriptions() As String =  New String(1) {"Parameter description."}  
  
            eventInfos.Add("MyCustomEvent", _  
              "Fires when my interesting event happens.", _  
              True, names, types, descriptions)  
  
        End Sub  
  
    End Class  
```  
  
<span data-ttu-id="c7ad9-123">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="c7ad9-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c7ad9-124">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c7ad9-125">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c7ad9-126">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ad9-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ad9-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7ad9-127">See Also</span></span>  
 <span data-ttu-id="c7ad9-128">[Integration Services&#40;SSIS&#41; 이벤트 처리기](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="c7ad9-128">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="c7ad9-129">패키지에 이벤트 처리기 추가</span><span class="sxs-lookup"><span data-stu-id="c7ad9-129">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
