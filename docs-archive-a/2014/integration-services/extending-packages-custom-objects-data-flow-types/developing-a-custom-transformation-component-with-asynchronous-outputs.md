---
title: 비동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], transformation components
- asynchronous outputs [Integration Services]
- ProcessInput method
- cache [Integration Services]
- buffer allocations [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], transformation components
ms.assetid: 1c3e92c7-a4fa-4fdd-b9ca-ac3069536274
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41e2ecdf9f90765e75ff2b8c9c0681a25366e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736610"
---
# <a name="developing-a-custom-transformation-component-with-asynchronous-outputs"></a><span data-ttu-id="6978a-102">비동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="6978a-102">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>
  <span data-ttu-id="6978a-103">변환이 구성 요소에서 입력 행을 모두 받을 때까지 행을 출력할 수 없거나 변환이 입력으로 받은 각 행에 대해 출력 행을 정확히 하나만 생성하지 않는 경우에는 비동기 출력을 사용하는 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-103">You use a component with asynchronous outputs when a transform cannot output rows until the component has received all its input rows, or when the transformation does not produce exactly one output row for each row received as input.</span></span> <span data-ttu-id="6978a-104">예를 들어 집계 변환은 행을 모두 읽기 전까지는 행 합계를 계산할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-104">The Aggregate transformation, for example, cannot calculate a sum across rows until it has read all the rows.</span></span> <span data-ttu-id="6978a-105">반면 각 데이터 행이 전달될 때 해당 행을 수정하는 경우에는 언제든지 동기 출력을 사용하는 구성 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-105">In contrast, you can use a component with synchronous outputs any time when you modify each row of data as it passes through.</span></span> <span data-ttu-id="6978a-106">각 행의 데이터를 현재 위치에서 수정하거나 각 입력 행의 값을 각각 포함하는 새 행을 하나 이상 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-106">You can modify the data for each row in place, or you can create one or more new columns, each of which has a value for every one of the input rows.</span></span> <span data-ttu-id="6978a-107">동기 구성 요소와 비동기 구성 요소 간의 차이점에 대한 자세한 내용은 [동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6978a-107">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="6978a-108">비동기 출력을 사용하는 변환 구성 요소는 대상 구성 요소와 원본 구성 요소 모두로 작동하므로 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-108">Transformation components with asynchronous outputs are unique because they act as both destination and source components.</span></span> <span data-ttu-id="6978a-109">이러한 종류의 구성 요소는 업스트림 구성 요소에서 행을 받고 다운스트림 구성 요소에서 사용되는 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-109">This kind of component receives rows from upstream components, and adds rows that are consumed by downstream components.</span></span> <span data-ttu-id="6978a-110">다른 데이터 흐름 구성 요소는 이 두 작업을 모두 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-110">No other data flow component performs both of these operations.</span></span>

 <span data-ttu-id="6978a-111">동기 출력을 사용하는 구성 요소에서 사용할 수 있는 업스트림 구성 요소의 열은 해당 구성 요소의 다운스트림 구성 요소에서도 자동으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-111">The columns from upstream components that are available to a component with synchronous outputs are automatically available to components downstream from the component.</span></span> <span data-ttu-id="6978a-112">따라서 동기 출력을 사용하는 구성 요소에서는 다음 구성 요소에 열과 행을 제공하기 위해 출력 열을 정의할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-112">Therefore, a component with synchronous outputs does not have to define any output columns to provide columns and rows to the next component.</span></span> <span data-ttu-id="6978a-113">반면 비동기 출력을 사용하는 구성 요소에서는 출력 열을 제공하고 다운스트림 구성 요소에 행을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-113">Components with asynchronous outputs, on the other hand, must define output columns and provide rows to downstream components.</span></span> <span data-ttu-id="6978a-114">따라서 비동기 출력을 사용하는 구성 요소에는 디자인 및 실행 시 수행해야 할 태스크가 더 많이 있으며 해당 구성 요소 개발자는 더 많은 코드를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-114">Therefore a component with asynchronous outputs has more tasks to perform during both design and execution time, and the component developer has more code to implement.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6978a-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에는 비동기 출력이 있는 몇 가지 변환이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains several transformations with asynchronous outputs.</span></span> <span data-ttu-id="6978a-116">예를 들어 정렬 변환의 경우에는 행을 정렬하기 전에 모든 행이 있어야 하며 행을 정렬하는 데는 비동기 출력이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-116">For example, the Sort transformation requires all its rows before it can sort them, and achieves this by using asynchronous outputs.</span></span> <span data-ttu-id="6978a-117">정렬 변환에서는 행을 모두 받은 후 이를 정렬하고 출력에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-117">After it has received all its rows, it sorts them and adds them to its output.</span></span>

 <span data-ttu-id="6978a-118">이 섹션에서는 비동기 출력을 사용하는 변환의 개발 방법을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-118">This section explains in detail how to develop transformations with asynchronous outputs.</span></span> <span data-ttu-id="6978a-119">원본 구성 요소 개발에 대한 자세한 내용은 [사용자 지정 원본 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6978a-119">For more information about source component development, see [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="6978a-120">디자인 타임</span><span class="sxs-lookup"><span data-stu-id="6978a-120">Design Time</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="6978a-121">구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="6978a-121">Creating the Component</span></span>
 <span data-ttu-id="6978a-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 개체의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 속성은 출력이 동기적인지 비동기적인지를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property on the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object identifies whether an output is synchronous or asynchronous.</span></span> <span data-ttu-id="6978a-123">비동기 출력을 만들려면 구성 요소에 출력을 추가하고 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A>를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-123">To create an asynchronous output, add the output to the component and set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> to zero.</span></span> <span data-ttu-id="6978a-124">이 속성을 설정하면 데이터 흐름 태스크에서 구성 요소의 입력과 출력 모두에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 개체를 할당할지, 아니면 단일 버퍼만 할당하여 두 개체 간에 이를 공유할지도 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-124">Setting this property also determines whether the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects for both the input and output of the component, or whether a single buffer is allocated and shared between the two objects.</span></span>

 <span data-ttu-id="6978a-125">다음 예제 코드에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 구현에서 비동기 출력을 만드는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-125">The following sample code shows a component that creates an asynchronous output in its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> implementation.</span></span>

```csharp
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "AsyncComponent",ComponentType = ComponentType.Transform)]
    public class AsyncComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Call the base class, which adds a synchronous input
            // and output.
            base.ProvideComponentProperties();

            // Make the output asynchronous.
            IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
            output.SynchronousInputID = 0;
        }
    }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime

<DtsPipelineComponent(DisplayName:="AsyncComponent", ComponentType:=ComponentType.Transform)> _
Public Class AsyncComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Call the base class, which adds a synchronous input
        ' and output.
        Me.ProvideComponentProperties()

        ' Make the output asynchronous.
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
        output.SynchronousInputID = 0

    End Sub

End Class
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="6978a-126">출력 열 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="6978a-126">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="6978a-127">앞에서 설명한 대로 비동기 구성 요소는 출력 열 컬렉션에 열을 추가하여 다운스트림 구성 요소에 열을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-127">As mentioned earlier, an asynchronous component adds columns to its output column collection to provide columns to downstream components.</span></span> <span data-ttu-id="6978a-128">디자인 타임에 선택할 수 있는 메서드는 구성 요소의 필요에 따라 몇 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-128">There are several design-time methods to choose from, depending on the needs of the component.</span></span> <span data-ttu-id="6978a-129">예를 들어 모든 열을 업스트림 구성 요소에서 다운스트림 구성 요소로 전달하려는 경우에는 구성 요소에서 입력 열을 사용할 수 있는 첫 번째 메서드가 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> 메서드이므로 이 메서드를 재정의하여 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-129">For example, if you want to pass all the columns from the upstream components to the downstream components, you would override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> method to add the columns, because this is the first method in which the input columns are available to the component.</span></span>

 <span data-ttu-id="6978a-130">구성 요소에서 입력에 대해 선택된 열을 기준으로 출력 열을 만드는 경우에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> 메서드를 재정의하여 출력 열을 선택하고 해당 열의 사용 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-130">If the component creates output columns based on the columns selected for its input, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> method to select the output columns and to indicate how they will be used.</span></span>

 <span data-ttu-id="6978a-131">비동기 출력을 사용하는 구성 요소에서 업스트림 구성 요소의 열을 기준으로 출력 열을 만들며 사용 가능한 업스트림 구성 요소가 변경되는 경우에는 구성 요소에서 출력 열 컬렉션을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-131">If a component with asynchronous outputs creates output columns based on the columns from upstream components, and the available upstream columns change, the component should update its output column collection.</span></span> <span data-ttu-id="6978a-132">구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>가 실행될 때 이러한 변경 내용을 검색하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>가 실행될 때 이를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-132">These changes should be detected by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and fixed during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>.</span></span>

> [!NOTE]
>  <span data-ttu-id="6978a-133">출력 열이 출력 열 컬렉션에서 제거되면 데이터 흐름에서 해당 열을 참조하는 다운스트림 구성 요소가 부정적인 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-133">When an output column is removed from the output column collection, downstream components in the data flow that reference the column are adversely affected.</span></span> <span data-ttu-id="6978a-134">다운스트림 구성 요소가 손상되지 않도록 하려면 출력 열을 제거하거나 다시 만들지 않고 해당 열을 복구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-134">The output column must be repaired without removing and recreating the column to prevent breaking the downstream components.</span></span> <span data-ttu-id="6978a-135">예를 들어 열의 데이터 형식이 변경된 경우에는 데이터 형식을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-135">For example, if the data type of the column has changed, you must update the data type.</span></span>

 <span data-ttu-id="6978a-136">다음 코드 예에서는 업스트림 구성 요소의 사용 가능한 각 열에 대해 해당 출력 열 컬렉션에 출력 열을 추가하는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-136">The following code example shows a component that adds an output column to its output column collection for each column available from the upstream component.</span></span>

```csharp
public override void OnInputPathAttached(int inputID)
{
   IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);
   IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
   IDTSVirtualInput100 vInput = input.GetVirtualInput();

   foreach (IDTSVirtualInputColumn100 vCol in vInput.VirtualInputColumnCollection)
   {
      IDTSOutputColumn100 outCol = output.OutputColumnCollection.New();
      outCol.Name = vCol.Name;
      outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage);
   }
}
```

```vb
Public Overrides Sub OnInputPathAttached(ByVal inputID As Integer)

    Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput()

    For Each vCol As IDTSVirtualInputColumn100 In vInput.VirtualInputColumnCollection

        Dim outCol As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        outCol.Name = vCol.Name
        outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage)

    Next
End Sub
```

## <a name="run-time"></a><span data-ttu-id="6978a-137">런타임</span><span class="sxs-lookup"><span data-stu-id="6978a-137">Run Time</span></span>
 <span data-ttu-id="6978a-138">또한 비동기 출력을 사용하는 구성 요소에서는 런타임에 다른 유형의 구성 요소와는 다른 일련의 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-138">Components with asynchronous outputs also execute a different sequence of methods at run time than other types of components.</span></span> <span data-ttu-id="6978a-139">먼저 이러한 구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드에 대한 호출을 모두 받는 유일한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-139">First, they are the only components that receive a call to both the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="6978a-140">또한 비동기 출력을 사용하는 구성 요소에서는 처리를 시작하기 전에 들어오는 모든 행에 액세스해야 하므로 모든 행을 읽기 전까지 입력 행을 내부에 캐시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-140">Components with asynchronous outputs also require access to all the incoming rows before they can start processing; therefore, they must cache the input rows internally until all rows have been read.</span></span> <span data-ttu-id="6978a-141">마지막으로 비동기 출력을 사용하는 구성 요소는 다른 구성 요소와 달리 입력 버퍼와 출력 버퍼를 모두 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-141">Finally, unlike other components, components with asynchronous outputs receive both an input buffer and an output buffer.</span></span>

### <a name="understanding-the-buffers"></a><span data-ttu-id="6978a-142">버퍼 이해</span><span class="sxs-lookup"><span data-stu-id="6978a-142">Understanding the Buffers</span></span>
 <span data-ttu-id="6978a-143">구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>이 실행될 때 입력 버퍼를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-143">The input buffer is received by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span> <span data-ttu-id="6978a-144">이 버퍼는 업스트림 구성 요소에서 버퍼에 추가한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-144">This buffer contains the rows added to the buffer by upstream components.</span></span> <span data-ttu-id="6978a-145">또한 업스트림 구성 요소의 출력에서 제공되었지만 비동기 구성 요소의 입력 컬렉션에 추가되지는 않은 열과 구성 요소의 입력 열도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-145">The buffer also contains the columns of the component's input, in addition to the columns that were provided in the output of an upstream component but were not added to the asynchronous component's input collection.</span></span>

 <span data-ttu-id="6978a-146"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>에서 구성 요소에 제공되는 출력 버퍼는 처음에는 행을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-146">The output buffer, which is provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, does not initially contain rows.</span></span> <span data-ttu-id="6978a-147">구성 요소는 이 버퍼에 행을 추가하고, 버퍼가 가득 차면 다운스트림 구성 요소에 버퍼를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-147">The component adds rows to this buffer and provides the buffer to downstream components when it is full.</span></span> <span data-ttu-id="6978a-148">출력 버퍼는 다른 다운스트림 구성 요소에서 자체 출력에 추가한 모든 열과 구성 요소의 출력 열 컬렉션에 정의된 열을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-148">The output buffer contains the columns defined in the component's output column collection, in addition to any columns that other downstream components have added to their outputs.</span></span>

 <span data-ttu-id="6978a-149">이와 달리 동기 출력을 사용하는 구성 요소에서는 단일 공유 버퍼를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-149">This is different behavior from that of components with synchronous outputs, which receive a single shared buffer.</span></span> <span data-ttu-id="6978a-150">동기 출력을 사용하는 구성 요소의 공유 버퍼는 업스트림 및 다운스트림 구성 요소의 출력에 추가된 열과 구성 요소의 입력 및 출력 열을 모두 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-150">The shared buffer of a component with synchronous outputs contains both the input and output columns of the component, in addition to columns added to the outputs of upstream and downstream components.</span></span>

### <a name="processing-rows"></a><span data-ttu-id="6978a-151">행 처리</span><span class="sxs-lookup"><span data-stu-id="6978a-151">Processing Rows</span></span>

#### <a name="caching-input-rows"></a><span data-ttu-id="6978a-152">입력 행 캐시</span><span class="sxs-lookup"><span data-stu-id="6978a-152">Caching Input Rows</span></span>
 <span data-ttu-id="6978a-153">비동기 출력을 사용하는 구성 요소를 작성할 때 출력 버퍼에 행을 추가하는 세 가지 방법 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-153">When you write a component with asynchronous outputs, you have three options for adding rows to the output buffer.</span></span> <span data-ttu-id="6978a-154">즉, 입력 행을 받을 때 행을 추가하거나, 구성 요소가 업스트림 구성 요소에서 모든 행을 받을 때까지 행을 캐시하거나, 구성 요소에 적절한 시기에 행을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-154">You can add them as input rows are received, you can cache them until the component has received all the rows from the upstream component, or you can add them when it is appropriate to do so for the component.</span></span> <span data-ttu-id="6978a-155">구성 요소의 요구 사항에 따라 다른 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-155">The method that you choose depends on the requirements of the component.</span></span> <span data-ttu-id="6978a-156">예를 들어 정렬 구성 요소의 경우에는 업스트림 행을 모두 받은 후에야 행을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-156">For example, the Sort component requires that all the upstream rows be received before they can be sorted.</span></span> <span data-ttu-id="6978a-157">따라서 모든 행을 읽을 때까지 기다렸다가 출력 버퍼에 행을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-157">Therefore, it waits until all rows have been read before adding rows to the output buffer.</span></span>

 <span data-ttu-id="6978a-158">입력 버퍼에서 받은 행은 구성 요소에서 처리할 준비가 될 때까지 내부에 캐시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-158">The rows that are received in the input buffer must be cached internally by the component until it is ready to process them.</span></span> <span data-ttu-id="6978a-159">들어오는 버퍼 행은 데이터 테이블, 다차원 배열 또는 그 밖의 내부 구조에 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-159">The incoming buffer rows can be cached in a data table, a multidimensional array, or any other internal structure.</span></span>

#### <a name="adding-output-rows"></a><span data-ttu-id="6978a-160">출력 행 추가</span><span class="sxs-lookup"><span data-stu-id="6978a-160">Adding Output Rows</span></span>
 <span data-ttu-id="6978a-161">행을 받을 때 출력 버퍼에 행을 추가하든 모든 행을 받은 후에 출력 버퍼에 행을 추가하든 항상 출력 버퍼에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-161">Whether you add rows to the output buffer as they are received or after receiving all of the rows, you do so by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method on the output buffer.</span></span> <span data-ttu-id="6978a-162">행을 추가한 후에는 새 행에서 각 열의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-162">After you have added the row, you set the values of each column in the new row.</span></span>

 <span data-ttu-id="6978a-163">출력 버퍼에는 구성 요소의 출력 열 컬렉션에 있는 것보다 많은 열이 있는 경우가 종종 있으므로 열 값을 설정하려면 먼저 버퍼에서 적절한 열의 인덱스를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-163">Because there are sometimes more columns in the output buffer than in the output column collection of the component, you must locate the index of the appropriate column in the buffer before you can set its value.</span></span> <span data-ttu-id="6978a-164"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 속성의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 메서드는 버퍼 행에서 지정된 계보 ID를 갖는 열 인덱스를 반환하며, 이 인덱스는 버퍼 열에 값을 할당하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-164">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property returns the index of the column in the buffer row with the specified lineage ID, which is then used to assign the value to the buffer column.</span></span>

 <span data-ttu-id="6978a-165"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 메서드는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드나 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드보다 먼저 호출되므로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 속성을 사용할 수 있으면서 입력 및 출력 버퍼에서 열 인덱스를 찾을 수 있는 첫 번째 메서드는 이 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-165">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, which is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method or the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, is the first method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property is available, and the first opportunity to locate the indexes of the columns in the input and output buffers.</span></span>

## <a name="sample"></a><span data-ttu-id="6978a-166">샘플</span><span class="sxs-lookup"><span data-stu-id="6978a-166">Sample</span></span>
 <span data-ttu-id="6978a-167">다음 예제에서는 비동기 출력을 사용하며 행을 받을 때 출력 버퍼에 행을 추가하는 간단한 변환 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-167">The following sample shows a simple transformation component with asynchronous outputs that adds rows to the output buffer as they are received.</span></span> <span data-ttu-id="6978a-168">이 예제는 이 항목에 설명된 메서드 및 기능의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-168">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="6978a-169">여기에서는 비동기 출력을 사용하는 모든 사용자 지정 변환 구성 요소에서 재정의해야 하는 중요한 메서드를 보여 주지만 디자인 타임 유효성 검사를 위한 코드는 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-169">It demonstrates the important methods that every custom transformation component with asynchronous outputs must override, but does not contain code for design-time validation.</span></span> <span data-ttu-id="6978a-170">또한 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>의 코드에서는 출력 열 컬렉션에 입력 열 컬렉션의 각 열에 대한 하나씩의 열이 있는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6978a-170">Also, the code in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> assumes that the output column collection has one column for each column in the input column collection.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
   [DtsPipelineComponent(DisplayName = "AsynchronousOutput")]
   public class AsynchronousOutput : PipelineComponent
   {
      PipelineBuffer outputBuffer;
      int[] inputColumnBufferIndexes;
      int[] outputColumnBufferIndexes;

      public override void ProvideComponentProperties()
      {
         // Let the base class add the input and output objects.
         base.ProvideComponentProperties();

         // Name the input and output, and make the
         // output asynchronous.
         ComponentMetaData.InputCollection[0].Name = "Input";
         ComponentMetaData.OutputCollection[0].Name = "AsyncOutput";
         ComponentMetaData.OutputCollection[0].SynchronousInputID = 0;
      }
      public override void PreExecute()
      {
         IDTSInput100 input = ComponentMetaData.InputCollection[0];
         IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

         inputColumnBufferIndexes = new int[input.InputColumnCollection.Count];
         outputColumnBufferIndexes = new int[output.OutputColumnCollection.Count];

         for (int col = 0; col < input.InputColumnCollection.Count; col++)
            inputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[col].LineageID);

         for (int col = 0; col < output.OutputColumnCollection.Count; col++)
            outputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[col].LineageID);

      }

      public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
      {
         if (buffers.Length != 0)
            outputBuffer = buffers[0];
      }
      public override void ProcessInput(int inputID, PipelineBuffer buffer)
      {
            // Advance the buffer to the next row.
            while (buffer.NextRow())
            {
               // Add a row to the output buffer.
               outputBuffer.AddRow();
               for (int x = 0; x < inputColumnBufferIndexes.Length; x++)
               {
                  // Copy the data from the input buffer column to the output buffer column.
                  outputBuffer[outputColumnBufferIndexes[x]] = buffer[inputColumnBufferIndexes[x]];
               }
            }
         if (buffer.EndOfRowset)
         {
            // EndOfRowset on the input buffer is true.
            // Set EndOfRowset on the output buffer.
            outputBuffer.SetEndOfRowset();
         }
      }
   }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

Namespace Microsoft.Samples.SqlServer.Dts

    <DtsPipelineComponent(DisplayName:="AsynchronousOutput")> _
    Public Class AsynchronousOutput

        Inherits PipelineComponent

        Private outputBuffer As PipelineBuffer
        Private inputColumnBufferIndexes As Integer()
        Private outputColumnBufferIndexes As Integer()

        Public Overrides Sub ProvideComponentProperties()

            ' Let the base class add the input and output objects.
            Me.ProvideComponentProperties()

            ' Name the input and output, and make the
            ' output asynchronous.
            ComponentMetaData.InputCollection(0).Name = "Input"
            ComponentMetaData.OutputCollection(0).Name = "AsyncOutput"
            ComponentMetaData.OutputCollection(0).SynchronousInputID = 0
        End Sub

        Public Overrides Sub PreExecute()

            Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)
            Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

            ReDim inputColumnBufferIndexes(input.InputColumnCollection.Count)
            ReDim outputColumnBufferIndexes(output.OutputColumnCollection.Count)

            For col As Integer = 0 To input.InputColumnCollection.Count
                inputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(col).LineageID)
            Next

            For col As Integer = 0 To output.OutputColumnCollection.Count
                outputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(col).LineageID)
            Next

        End Sub
        Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

            If buffers.Length <> 0 Then
                outputBuffer = buffers(0)
            End If

        End Sub

        Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)

                ' Advance the buffer to the next row.
                While (buffer.NextRow())

                    ' Add a row to the output buffer.
                    outputBuffer.AddRow()
                    For x As Integer = 0 To inputColumnBufferIndexes.Length

                        ' Copy the data from the input buffer column to the output buffer column.
                        outputBuffer(outputColumnBufferIndexes(x)) = buffer(inputColumnBufferIndexes(x))

                    Next
                End While

            If buffer.EndOfRowset = True Then
                ' EndOfRowset on the input buffer is true.
                ' Set the end of row set on the output buffer.
                outputBuffer.SetEndOfRowset()
            End If
        End Sub
    End Class
End Namespace
```

<span data-ttu-id="6978a-171">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6978a-171">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6978a-172">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6978a-172">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6978a-173">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6978a-173">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6978a-174">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6978a-174">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="6978a-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6978a-175">See Also</span></span>
 <span data-ttu-id="6978a-176">[동기 출력을 사용 하 여 사용자 지정 변환 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) [동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md) [스크립트 구성 요소를 사용 하 여 비동기 변환 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="6978a-176">[Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span></span>


