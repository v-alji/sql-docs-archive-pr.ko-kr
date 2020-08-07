---
title: 데이터 흐름 구성 요소의 런타임 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- run-time [Integration Services]
- data flow components [Integration Services], run-time methods
ms.assetid: fd9e4317-18dd-43af-bbdc-79db32183ac4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df0afe4c29044541c5a57aa3a466283ab4fe4fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734371"
---
# <a name="run-time-methods-of-a-data-flow-component"></a><span data-ttu-id="81768-102">데이터 흐름 구성 요소의 런타임 메서드</span><span class="sxs-lookup"><span data-stu-id="81768-102">Run-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="81768-103">런타임에 데이터 흐름 태스크에서는 구성 요소의 시퀀스를 검사하고, 실행 계획을 준비하고, 작업 계획을 실행하는 작업자 스레드의 풀을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-103">At run time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="81768-104">또한 원본에서 데이터 행을 로드하고 이를 변환을 통해 처리한 다음 대상에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-104">The task loads rows of data from sources, processes them through transformations, then saves them to destinations.</span></span>  
  
## <a name="sequence-of-method-execution"></a><span data-ttu-id="81768-105">메서드 실행 순서</span><span class="sxs-lookup"><span data-stu-id="81768-105">Sequence of Method Execution</span></span>  
 <span data-ttu-id="81768-106">데이터 흐름 구성 요소를 실행하는 동안에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 기본 클래스에 포함된 일련의 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-106">During the execution of a data flow component, a subset of the methods in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is called.</span></span> <span data-ttu-id="81768-107">이러한 메서드와 메서드가 호출되는 순서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드만 제외하고 항상 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-107">The methods, and the sequence in which they are called, are always the same, with the exception of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="81768-108">이 두 메서드가 호출되는 방식은 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 개체가 있는지 여부와 해당 구성에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="81768-108">These two methods are called based on the existence and configuration of a component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> objects.</span></span>  
  
 <span data-ttu-id="81768-109">다음 목록에서는 구성 요소가 실행되는 동안 호출되는 메서드를 호출 순서대로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81768-109">The following list shows the methods in the order in which they are called during component execution.</span></span> <span data-ttu-id="81768-110"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>이 호출될 때는 항상 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>보다 먼저 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-110">Note that <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, when called, is always called before <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrepareForExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PostExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Cleanup%2A>  
  
### <a name="primeoutput-method"></a><span data-ttu-id="81768-111">PrimeOutput 메서드</span><span class="sxs-lookup"><span data-stu-id="81768-111">PrimeOutput Method</span></span>  
 <span data-ttu-id="81768-112"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> 메서드는 구성 요소에 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 개체를 통해 다운스트림 구성 요소에 연결된 출력이 하나 이상 있고 이 출력의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 속성이 0인 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-112">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called when a component has at least one output, attached to a downstream component through an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, and the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property of the output is zero.</span></span> <span data-ttu-id="81768-113">비동기 출력을 사용하는 원본 구성 요소 및 변환의 경우에는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A>이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-113">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called for source components and for transformations with asynchronous outputs.</span></span> <span data-ttu-id="81768-114">아래에 설명된 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드와 달리 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드는 해당 메서드가 필요한 각 구성 요소에 대해 한 번씩만 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-114">Unlike the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method described below, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is only called once for each component that requires it.</span></span>  
  
### <a name="processinput-method"></a><span data-ttu-id="81768-115">ProcessInput 메서드</span><span class="sxs-lookup"><span data-stu-id="81768-115">ProcessInput Method</span></span>  
 <span data-ttu-id="81768-116"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> 메서드는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 개체를 통해 업스트림 구성 요소에 연결된 하나 이상의 입력이 있는 구성 요소에 대해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for components that have at least one input attached to an upstream component by an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object.</span></span> <span data-ttu-id="81768-117"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> 메서드는 대상 구성 요소와 동기 출력을 사용하는 변환에 대해 호출됩니다</span><span class="sxs-lookup"><span data-stu-id="81768-117">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for destination components and for transformations with synchronous outputs.</span></span> <span data-ttu-id="81768-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>은 업스트림 구성 요소에서 더 이상 처리할 행이 없을 때까지 반복적으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> is called repeatedly until there are no more rows to process from upstream components.</span></span>  
  
## <a name="working-with-inputs-and-outputs"></a><span data-ttu-id="81768-119">입/출력 작업</span><span class="sxs-lookup"><span data-stu-id="81768-119">Working with Inputs and Outputs</span></span>  
 <span data-ttu-id="81768-120">런타임에 데이터 흐름 구성 요소에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-120">At run time, data flow components perform the following tasks:</span></span>  
  
-   <span data-ttu-id="81768-121">원본 구성 요소가 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-121">Source components add rows.</span></span>  
  
-   <span data-ttu-id="81768-122">동기 출력을 사용하는 변환 구성 요소가 원본 구성 요소에서 제공된 행을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="81768-122">Transformation components with synchronous outputs receive rows provided by source components.</span></span>  
  
-   <span data-ttu-id="81768-123">비동기 출력을 사용하는 변환 구성 요소가 행을 받고 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-123">Transformation components with asynchronous outputs receive rows and add rows.</span></span>  
  
-   <span data-ttu-id="81768-124">대상 구성 요소가 행을 받은 다음 대상으로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-124">Destination components receive rows and then load them into a destination.</span></span>  
  
 <span data-ttu-id="81768-125">실행 중 데이터 흐름 태스크에서는 구성 요소 시퀀스의 출력 열 컬렉션에 정의된 모든 열이 포함된 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-125">During execution, the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain all the columns defined in the output column collections of a sequence of components.</span></span> <span data-ttu-id="81768-126">예를 들어 데이터 흐름 시퀀스에 있는 네 개의 구성 요소가 각각 해당 출력 열 컬렉션에서 출력 열을 하나씩 추가할 경우 각 구성 요소에 제공된 버퍼에는 이 네 개의 출력 열이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-126">For example, if each of four components in a data flow sequence adds one output column to its output column collection,the buffer that is provided to each component contains four columns, one for each output column per component.</span></span> <span data-ttu-id="81768-127">이 동작으로 인해 구성 요소가 받는 버퍼에 해당 구성 요소에서 사용하지 않는 열이 포함된 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81768-127">Because of this behavior, a component sometimes receives buffers that contain columns it does not use.</span></span>  
  
 <span data-ttu-id="81768-128">구성 요소가 받는 버퍼에는 해당 구성 요소에서 사용하지 않는 열이 포함되는 경우가 있으므로 구성 요소의 입력 및 출력 열 컬렉션에 사용할 열은 데이터 흐름 태스크가 해당 구성 요소에 제공한 버퍼에서 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-128">Since the buffers received by your component may contain columns that the component will not use, you must locate the columns that you want to use in your component's input and output column collections in the buffer provided to the component by the data flow task.</span></span> <span data-ttu-id="81768-129">이렇게 하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 속성의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-129">You do this by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property.</span></span> <span data-ttu-id="81768-130">성능상의 이유로 이 태스크는 일반적으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 또는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 대신 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-130">For performance reasons, this task is ordinarily performed during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, rather than in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
 <span data-ttu-id="81768-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드보다 먼저 호출되므로 구성 요소에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>를 사용할 수 있게 된 후 이 작업을 수행할 수 있는 첫 번째 메서드는 이 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="81768-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods, and is the first opportunity for a component to perform this work after the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> becomes available to the component.</span></span> <span data-ttu-id="81768-132">이 메서드가 실행될 때 구성 요소는 버퍼에서 해당 구성 요소의 열을 찾고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 또는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드에서 해당 열을 사용할 수 있도록 이 정보를 내부에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-132">During this method, the component should locate its columns in the buffers and store this information internally so the columns can be used in either the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span>  
  
 <span data-ttu-id="81768-133">다음 코드 예에서는 동기 출력을 사용하는 변환 구성 요소가 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 실행 중 버퍼에서 입력 열을 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81768-133">The following code example demonstrates how a transformation component with a synchronous output locates its input columns in the buffer during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span>  
  
```csharp  
private int []bufferColumnIndex;  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    bufferColumnIndex = new int[input.InputColumnCollection.Count];  
  
    for( int x=0; x < input.InputColumnCollection.Count; x++)  
    {  
        IDTSInputColumn100 column = input.InputColumnCollection[x];  
        bufferColumnIndex[x] = BufferManager.FindColumnByLineageID( input.Buffer, column.LineageID);  
    }  
}  
```  
  
```vb  
Dim bufferColumnIndex As Integer()  
  
    Public Overrides Sub PreExecute()  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
        ReDim bufferColumnIndex(input.InputColumnCollection.Count)  
  
        For x As Integer = 0 To input.InputColumnCollection.Count  
  
            Dim column As IDTSInputColumn100 = input.InputColumnCollection(x)  
            bufferColumnIndex(x) = BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID)  
  
        Next  
  
    End Sub  
```  
  
### <a name="adding-rows"></a><span data-ttu-id="81768-134">행 추가</span><span class="sxs-lookup"><span data-stu-id="81768-134">Adding Rows</span></span>  
 <span data-ttu-id="81768-135">구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 개체에 행을 추가하는 방법으로 다운스트림 구성 요소에 행을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-135">Components supply rows to downstream components by adding rows to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="81768-136">데이터 흐름 태스크에서는 다운스트림 구성 요소에 연결된 각 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 개체에 대한 출력 버퍼가 하나씩 포함된 출력 버퍼 배열을 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드에 대한 매개 변수로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-136">The data flow task provides an array of output buffers - one for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that is connected to a downstream component - as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="81768-137">원본 구성 요소와 비동기 출력을 사용하는 변환 구성 요소에서는 버퍼에 행을 추가하고 행 추가가 완료되면 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-137">Source components and transformation components with asynchronous outputs add rows to the buffers and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method when they are finished adding rows.</span></span> <span data-ttu-id="81768-138">데이터 흐름 태스크에서는 해당 태스크가 구성 요소에 제공한 출력 버퍼를 관리하고 버퍼가 가득 차면 해당 버퍼의 행을 자동으로 다음 구성 요소로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-138">The data flow task manages the output buffers that it supplies to components and, as a buffer becomes full, automatically moves the rows in the buffer to the next component.</span></span> <span data-ttu-id="81768-139"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드는 반복적으로 호출되는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드와 달리 구성 요소마다 한 번씩 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-139">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is called one time per component, unlike  the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, which is called repeatedly.</span></span>  
  
 <span data-ttu-id="81768-140">다음 코드 예에서는 구성 요소에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드 실행 중 출력 버퍼에 행을 추가한 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 메서드를 호출하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81768-140">The following code example demonstrates how a component adds rows to its output buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method, then calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method.</span></span>  
  
```csharp  
public override void PrimeOutput( int outputs, int []outputIDs,PipelineBuffer []buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        IDTSOutput100 output = ComponentMetaData.OutputCollection.GetObjectByID( outputIDs[x]);  
        PipelineBuffer buffer = buffers[x];  
  
        // TODO: Add rows to the output buffer.  
    }  
    foreach( PipelineBuffer buffer in buffers )  
    {  
        /// Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset();  
    }  
}  
```  
  
```vb  
public overrides sub PrimeOutput( outputs as Integer , outputIDs() as Integer ,buffers() as PipelineBuffer buffers)  
  
    For x As Integer = 0 To outputs.MaxValue  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.GetObjectByID(outputIDs(x))  
        Dim buffer As PipelineBuffer = buffers(x)  
  
        ' TODO: Add rows to the output buffer.  
  
    Next  
  
    For Each buffer As PipelineBuffer In buffers  
  
        ' Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset()  
  
    Next  
  
End Sub  
```  
  
 <span data-ttu-id="81768-141">출력 버퍼에 행을 추가하는 구성 요소 개발에 대한 자세한 내용은 [사용자 지정 원본 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) 및 [비동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81768-141">For more information about developing components that add rows to output buffers, see [Developing a Custom Source Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) and [Developing a Custom Transformation Component with Asynchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).</span></span>  
  
### <a name="receiving-rows"></a><span data-ttu-id="81768-142">파일 받기</span><span class="sxs-lookup"><span data-stu-id="81768-142">Receiving Rows</span></span>  
 <span data-ttu-id="81768-143">구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 개체에서 업스트림 구성 요소의 행을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="81768-143">Components receive rows from upstream components in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="81768-144">데이터 흐름 태스크에서는 업스트림 구성 요소가 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 메서드에 대한 매개 변수로 데이터 흐름에 추가한 행이 들어 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-144">The data flow task provides a <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> object that contains the rows added to the data flow by upstream components as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="81768-145">이 입력 버퍼를 사용하여 버퍼의 행 및 열을 검사하거나 수정할 수 있지만 행을 추가하거나 제거할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81768-145">This input buffer can be used to examine and modify the rows and columns in the buffer, but cannot be used to add or remove rows.</span></span> <span data-ttu-id="81768-146"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드는 사용할 수 없는 버퍼가 더 이상 없을 때까지 반복적으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-146">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method is called repeatedly until there are no more available buffers.</span></span> <span data-ttu-id="81768-147">이 메서드가 마지막으로 호출될 때는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 속성이 `true`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="81768-147">The last time it is called, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property is `true`.</span></span> <span data-ttu-id="81768-148">버퍼 내에서 다음 행으로 진행하는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> 메서드를 사용하면 버퍼의 행 컬렉션을 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81768-148">You can iterate over the collection of rows in the buffer by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method, which advances the buffer to the next row.</span></span> <span data-ttu-id="81768-149">버퍼가 컬렉션의 마지막 행에 있으면 이 메서드는 `false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81768-149">This method returns `false` when the buffer is on the last row in the collection.</span></span> <span data-ttu-id="81768-150">마지막 데이터 행이 처리된 후 추가 동작을 수행해야 하는 경우가 아니면 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 속성을 확인할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81768-150">You do not have to check the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property unless you have to perform an additional action after the last rows of data have been processed.</span></span>  
  
 <span data-ttu-id="81768-151">다음 텍스트는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> 메서드와 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 속성을 사용할 때 올바른 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81768-151">The following text shows the correct pattern for using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property:</span></span>  
  
 `while (buffer.NextRow())`  
  
 `{`  
  
 `// Do something with each row.`  
  
 `}`  
  
 `if (buffer.EndOfRowset)`  
  
 `{`  
  
 `// Optionally, do something after all rows have been processed.`  
  
 `}`  
  
 <span data-ttu-id="81768-152">다음 코드 예에서는 구성 요소에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드 실행 중 입력 버퍼의 행을 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81768-152">The following code example demonstrates how a component processes the rows in input buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span>  
  
```csharp  
public override void ProcessInput( int inputID, PipelineBuffer buffer )  
{  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
        while( buffer.NextRow())  
        {  
            // TODO: Examine the columns in the current row.  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
        While buffer.NextRow() = True  
  
            ' TODO: Examine the columns in the current row.  
        End While  
  
End Sub  
```  
  
 <span data-ttu-id="81768-153">입력 버퍼에 행을 받는 구성 요소 개발에 대한 자세한 내용은 [사용자 지정 원본 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) 및 [동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81768-153">For more information about developing components that receive rows in input buffers, see [Developing a Custom Destination Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) and [Developing a Custom Transformation Component with Synchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>  
  
<span data-ttu-id="81768-154">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="81768-154">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="81768-155">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="81768-155">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="81768-156">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="81768-156">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="81768-157">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="81768-157">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81768-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81768-158">See Also</span></span>  
 [<span data-ttu-id="81768-159">데이터 흐름 구성 요소의 디자인 타임 메서드</span><span class="sxs-lookup"><span data-stu-id="81768-159">Design-time Methods of a Data Flow Component</span></span>](design-time-methods-of-a-data-flow-component.md)  
  
  
