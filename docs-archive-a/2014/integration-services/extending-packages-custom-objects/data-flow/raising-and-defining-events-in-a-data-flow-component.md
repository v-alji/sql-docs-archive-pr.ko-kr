---
title: 데이터 흐름 구성 요소에서 이벤트 발생 및 정의 | Microsoft Docs
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
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f4572f8a8af829145da4e4d685f5dddad4a29a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729643"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a><span data-ttu-id="4d9ab-102">데이터 흐름 구성 요소에서 이벤트 발생 및 정의</span><span class="sxs-lookup"><span data-stu-id="4d9ab-102">Raising and Defining Events in a Data Flow Component</span></span>
  <span data-ttu-id="4d9ab-103">구성 요소 개발자는 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 속성에 제공된 메서드를 호출하여 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 인터페이스에 정의된 일부 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-103">Component developers can raise a subset of the events defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface by calling the methods exposed on the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="4d9ab-104"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> 컬렉션을 사용하여 사용자 지정 이벤트를 정의하고 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 메서드를 사용하여 실행하는 동안 해당 이벤트를 발생시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-104">You can also define custom events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection, and raise them during execution by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="4d9ab-105">이 섹션에서는 이벤트를 만들고 발생시키는 방법을 설명하고 디자인 타임에 이벤트를 발생시켜야 하는 경우에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-105">This section describes how to create and raise an event, and provides guidelines on when you should raise events at design time.</span></span>

## <a name="raising-events"></a><span data-ttu-id="4d9ab-106">이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="4d9ab-106">Raising Events</span></span>
 <span data-ttu-id="4d9ab-107">구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스의 **Fire\<X>** 메서드를 사용하여 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-107">Components raise events by using the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="4d9ab-108">구성 요소를 디자인하거나 실행할 때 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-108">You can raise events during component design and execution.</span></span> <span data-ttu-id="4d9ab-109">일반적으로 구성 요소를 디자인할 때는 유효성 검사 과정에서 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-109">Typically, during component design, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> methods are called during validation.</span></span> <span data-ttu-id="4d9ab-110">이러한 이벤트는 구성 요소가 잘못 구성되어 있는 경우 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 **오류 목록** 창에 메시지를 표시하고 구성 요소 사용자에게 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-110">These events display messages in the **Error List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and provide feedback to users of the component when a component is incorrectly configured.</span></span>

 <span data-ttu-id="4d9ab-111">또한 구성 요소에서는 실행 중 어느 시점에서나 이벤트를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-111">Components can also raise events at any point during execution.</span></span> <span data-ttu-id="4d9ab-112">구성 요소 개발자는 이벤트를 통해 구성 요소가 실행될 때 구성 요소 사용자에게 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-112">Events allow component developers to provide feedback to users of the component as it executes.</span></span> <span data-ttu-id="4d9ab-113">실행 중 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> 메서드를 호출하면 패키지가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-113">Calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> method during execution is likely to fail the package.</span></span>

## <a name="defining-and-raising-custom-events"></a><span data-ttu-id="4d9ab-114">사용자 지정 이벤트 정의 및 발생</span><span class="sxs-lookup"><span data-stu-id="4d9ab-114">Defining and Raising Custom Events</span></span>

### <a name="defining-a-custom-event"></a><span data-ttu-id="4d9ab-115">사용자 지정 이벤트 정의</span><span class="sxs-lookup"><span data-stu-id="4d9ab-115">Defining a Custom Event</span></span>
 <span data-ttu-id="4d9ab-116">사용자 지정 이벤트는 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> 메서드를 호출하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-116">Custom events are created by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection.</span></span> <span data-ttu-id="4d9ab-117">이 컬렉션은 데이터 흐름 태스크에서 설정되며 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 기본 클래스를 통해 구성 요소 개발자에게 속성으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-117">This collection is set by the data flow task and provided as a property to the component developer through the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class.</span></span> <span data-ttu-id="4d9ab-118">이 클래스에는 데이터 흐름 태스크에서 정의된 사용자 지정 이벤트와 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 메서드 실행 중 구성 요소에서 정의된 사용자 지정 이벤트가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-118">This class contains custom events defined by the data flow task and custom events defined by the component during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method.</span></span>

 <span data-ttu-id="4d9ab-119">구성 요소의 사용자 지정 이벤트는 패키지 XML에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-119">The custom events of a component are not persisted in the package XML.</span></span> <span data-ttu-id="4d9ab-120">따라서 구성 요소가 해당 구성 요소에서 발생하는 이벤트를 정의할 수 있도록 디자인할 때와 실행할 때 모두 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-120">Therefore, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method is called during both design and execution to allow the component to define the events it raises.</span></span>

 <span data-ttu-id="4d9ab-121"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> 메서드의 *allowEventHandlers* 매개 변수는 구성 요소에서 이벤트에 대한 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 개체를 만들 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-121">The *allowEventHandlers* parameter of the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method specifies whether the component allows <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects to be created for the event.</span></span> <span data-ttu-id="4d9ab-122"><xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers>는 동기 개체이므로</span><span class="sxs-lookup"><span data-stu-id="4d9ab-122">Note that <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> are synchronous.</span></span> <span data-ttu-id="4d9ab-123">구성 요소에서는 사용자 지정 이벤트에 연결된 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>가 실행을 마칠 때까지 실행을 다시 시작하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-123">Therefore the component does not resume execution until an <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> attached to the custom event has finished executing.</span></span> <span data-ttu-id="4d9ab-124">*AllowEventHandlers* 매개 변수가 인 경우 `true` <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 런타임에 의해 자동으로 만들어지고 채워지는 변수를 통해 모든 개체에서 이벤트의 각 매개 변수를 사용할 수 있게 됩니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d9ab-124">If the *allowEventHandlers* parameter is `true`, each parameter of the event is automatically made available to any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects through variables that are created and populated automatically by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

### <a name="raising-a-custom-event"></a><span data-ttu-id="4d9ab-125">사용자 지정 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="4d9ab-125">Raising a Custom Event</span></span>
 <span data-ttu-id="4d9ab-126">구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 메서드를 호출하고 이벤트의 이름, 텍스트 및 매개 변수를 제공하여 사용자 지정 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-126">Components raise custom events by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method, and providing the name, text, and parameters of the event.</span></span> <span data-ttu-id="4d9ab-127">*AllowEventHandlers* 매개 변수가 이면 `true` <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> 사용자 지정 이벤트에 대해 만들어진 모든가 런타임 엔진에 의해 실행 됩니다 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d9ab-127">If the *allowEventHandlers* parameter is `true`, any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> that are created for the custom event are executed by the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] run-time engine.</span></span>

### <a name="custom-event-sample"></a><span data-ttu-id="4d9ab-128">사용자 지정 이벤트 예제</span><span class="sxs-lookup"><span data-stu-id="4d9ab-128">Custom Event Sample</span></span>
 <span data-ttu-id="4d9ab-129">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 메서드 실행 중 사용자 지정 이벤트를 정의한 다음 런타임에 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 메서드를 호출하여 이벤트를 발생시키는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-129">The following code example shows a component that defines a custom event during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method, and then raises the event at run time by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span>

```csharp
public override void RegisterEvents()
{
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);
}
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
    while (buffer.NextRow())
    {
       // Process buffer rows.
    }

    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);
}
```

```vb
Public  Overrides Sub RegisterEvents() 
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"} 
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)} 
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."} 
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions) 
End Sub 

Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
  While buffer.NextRow 
  End While 
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort") 
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now} 
  ComponentMetaData.FireCustomEvent("StartingSort", _
    "Beginning sort operation.", arguments, _
    ComponentMetaData.Name, FireSortEventAgain) 
End Sub
```

<span data-ttu-id="4d9ab-130">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4d9ab-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4d9ab-131">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4d9ab-132">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4d9ab-133">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="4d9ab-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d9ab-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d9ab-134">See Also</span></span>
 <span data-ttu-id="4d9ab-135">[INTEGRATION SERVICES SSIS&#41; 이벤트 처리기 &#40;](../../integration-services-ssis-event-handlers.md) [패키지에 이벤트 처리기 추가](../../add-an-event-handler-to-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="4d9ab-135">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) [Add an Event Handler to a Package](../../add-an-event-handler-to-a-package.md)</span></span>


