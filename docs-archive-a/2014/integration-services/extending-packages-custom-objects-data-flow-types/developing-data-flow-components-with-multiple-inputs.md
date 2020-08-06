---
title: 여러 입력을 지원하는 데이터 흐름 구성 요소 개발 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb56878c1b1b68dfdc4de19cb2b811de494c761b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736604"
---
# <a name="developing-data-flow-components-with-multiple-inputs"></a><span data-ttu-id="8b37f-102">여러 입력을 지원하는 데이터 흐름 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="8b37f-102">Developing Data Flow Components with Multiple Inputs</span></span>
  <span data-ttu-id="8b37f-103">여러 입력을 지원하는 데이터 흐름 구성 요소는 여러 입력에서 데이터가 생성되는 속도가 균일하지 않을 경우 과도한 메모리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-103">A data flow component with multiple inputs may consume excessive memory if its multiple inputs produce data at uneven rates.</span></span> <span data-ttu-id="8b37f-104">둘 이상의 입력을 지원하는 사용자 지정 데이터 흐름 구성 요소를 개발한 경우 Microsoft.SqlServer.Dts.Pipeline 네임스페이스의 다음 멤버를 사용하여 이로 인한 메모리 가중을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-104">When you develop a custom data flow component that supports two or more inputs, you can manage this memory pressure by using the following members in the Microsoft.SqlServer.Dts.Pipeline namespace:</span></span>  
  
-   <span data-ttu-id="8b37f-105"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 속성 -</span><span class="sxs-lookup"><span data-stu-id="8b37f-105">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> class.</span></span> <span data-ttu-id="8b37f-106">사용자 지정 데이터 흐름 구성 요소에서 속도가 균일하지 않은 데이터를 관리하는 데 필요한 코드를 구현하려면 이 속성 값을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-106">Set the value of this property to `true` if you want to implement the code that is necessary for your custom data flow component to manage data flowing at uneven rates.</span></span>  
  
-   <span data-ttu-id="8b37f-107"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드 -</span><span class="sxs-lookup"><span data-stu-id="8b37f-107">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span> <span data-ttu-id="8b37f-108"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 속성을 `true`로 설정한 경우 이 메서드의 구현을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-108">You must provide an implementation of this method if you set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true`.</span></span> <span data-ttu-id="8b37f-109">그러지 않으면 데이터 흐름 엔진에서 런타임 시 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-109">If you do not provide an implementation, the data flow engine raises an exception at run time.</span></span>  
  
-   <span data-ttu-id="8b37f-110"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드 -</span><span class="sxs-lookup"><span data-stu-id="8b37f-110">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span> <span data-ttu-id="8b37f-111"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 속성을 `true`로 설정하고 사용자 지정 구성 요소가 세 개 이상의 입력을 지원하는 경우에는 이 메서드의 구현도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-111">You must also provide an implementation of this method if you set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` and your custom component supports more than two inputs.</span></span> <span data-ttu-id="8b37f-112">그러지 않으면 사용자가 세 개 이상의 입력을 연결할 경우 데이터 흐름 엔진에서 런타임 시 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-112">If you do not provide an implementation, the data flow engine raises an exception at run time if the user attaches more than two inputs.</span></span>  
  
 <span data-ttu-id="8b37f-113">이러한 멤버를 함께 사용하여 Microsoft에서 병합 및 병합 조인 변환을 위해 개발한 솔루션과 유사한 메모리 가중 관리 솔루션을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-113">Together, these members enable you to develop a solution for memory pressure that is similar to the solution that Microsoft developed for the Merge and Merge Join transformations.</span></span>  
  
## <a name="setting-the-supportsbackpressure-property"></a><span data-ttu-id="8b37f-114">SupportsBackPressure 속성 설정</span><span class="sxs-lookup"><span data-stu-id="8b37f-114">Setting the SupportsBackPressure Property</span></span>  
 <span data-ttu-id="8b37f-115">여러 입력을 지원하는 사용자 지정 데이터 흐름 구성 요소의 메모리 관리 성능을 향상시키는 첫 번째 단계는 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A>에서 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 속성을 `true`로 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-115">The first step in implementing better memory management for a custom data flow component that supports multiple inputs is to set the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="8b37f-116"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 값이 `true`인 경우 데이터 흐름 엔진은 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 메서드를 호출하며, 입력이 세 개 이상인 경우 런타임에 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드도 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-116">When the value of <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> is `true`, the data flow engine calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method and, when there are more than two inputs, also calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method at run time.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8b37f-117">예제</span><span class="sxs-lookup"><span data-stu-id="8b37f-117">Example</span></span>  
 <span data-ttu-id="8b37f-118">다음 예에서 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>의 구현은 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 값을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-118">In the following example, the implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> sets the value of <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> to `true`.</span></span>  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a><span data-ttu-id="8b37f-119">IsInputReady 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="8b37f-119">Implementing the IsInputReady Method</span></span>  
 <span data-ttu-id="8b37f-120"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> 개체에서 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 속성 값을 `true`로 설정한 경우 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드에 대한 구현도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-120">When you set the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> property to `true` in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> object, you must also provide an implementation for the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b37f-121"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 메서드의 구현은 기본 클래스의 구현을 호출해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-121">Your implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method should not call the implementations in the base class.</span></span> <span data-ttu-id="8b37f-122">기본 클래스의 이 메서드에 대한 기본 구현은 `NotImplementedException`만 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-122">The default implementation of this method in the base class simply raises a `NotImplementedException`.</span></span>  
  
 <span data-ttu-id="8b37f-123">이 메서드를 구현할 때는 구성 요소의 각 입력에 대해 요소 상태를 부울 *canProcess* 배열로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-123">When you implement this method, you set the status of an element in the Boolean *canProcess* array for each of the component's inputs.</span></span> <span data-ttu-id="8b37f-124">입력은 *inputIDs* 배열에서 해당 ID 값으로 식별 됩니다. 입력에 대해 *Canprocess* 배열의 요소 값을로 설정 하면 `true` 데이터 흐름 엔진에서 구성 요소의 메서드를 호출 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 하 고 지정 된 입력에 더 많은 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-124">(The inputs are identified by their ID values in the *inputIDs* array.) When you set the value of an element in the *canProcess* array to `true` for an input, the data flow engine calls the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method and provides more data for the specified input.</span></span>  
  
 <span data-ttu-id="8b37f-125">더 많은 업스트림 데이터를 사용할 수 있지만 하나 이상의 입력에 대 한 *Canprocess* 배열 요소의 값은 항상 `true` 이거나 처리가 중지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-125">While more upstream data is available, the value of the *canProcess* array element for at least one input must always be `true`, or processing stops.</span></span>  
  
 <span data-ttu-id="8b37f-126">데이터 흐름 엔진은 추가 데이터를 받기 위해 대기 중인 입력을 확인하기 위해 각 데이터 버퍼를 보내기 전에 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-126">The data flow engine calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method before sending each buffer of data to determine which inputs are waiting to receive more data.</span></span> <span data-ttu-id="8b37f-127">입력이 차단되었음을 나타내는 값이 반환된 경우 데이터 흐름 엔진은 해당 입력에 대한 추가 데이터 버퍼를 구성 요소에 보내는 대신 일시적으로 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-127">When the return value indicates that an input is blocked, the data flow engine temporarily caches additional buffers of data for that input instead of sending them to the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b37f-128">사용자가 작성한 코드에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 또는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드를 호출하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-128">You do not call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> methods in your own code.</span></span> <span data-ttu-id="8b37f-129">이러한 메서드와 사용자가 재정의한 `PipelineComponent` 클래스의 다른 메서드는 사용자의 구성 요소를 실행할 때 데이터 흐름 엔진에서 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-129">The data flow engine calls these methods, and the other methods of the `PipelineComponent` class that you override, when the data flow engine runs your component.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8b37f-130">예제</span><span class="sxs-lookup"><span data-stu-id="8b37f-130">Example</span></span>  
 <span data-ttu-id="8b37f-131">다음 예에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 메서드의 구현은 다음 조건을 충족하는 경우 입력이 추가 데이터를 받기 위해 대기 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-131">In the following example, the implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that an input is waiting to receive more data when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="8b37f-132">추가 업스트림 데이터를 입력에 사용할 수 있는 경우(`!inputEOR`)</span><span class="sxs-lookup"><span data-stu-id="8b37f-132">More upstream data is available for the input (`!inputEOR`).</span></span>  
  
-   <span data-ttu-id="8b37f-133">구성 요소에서 이미 받은 버퍼에 현재 입력에 대해 처리할 수 있는 데이터가 없는 경우(`inputBuffers[inputIndex].CurrentRow() == null`)</span><span class="sxs-lookup"><span data-stu-id="8b37f-133">The component does not currently have data available to process for the input in the buffers that the component has already received (`inputBuffers[inputIndex].CurrentRow() == null`).</span></span>  
  
 <span data-ttu-id="8b37f-134">입력이 추가 데이터를 받기 위해 대기 중인 경우 데이터 흐름 구성 요소는 `true` 해당 입력에 해당 하는 *canprocess* 배열의 요소 값을로 설정 하 여이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-134">If an input is waiting to receive more data, the data flow component indicates this by setting to `true` the value of the element in the *canProcess* array that corresponds to that input.</span></span>  
  
 <span data-ttu-id="8b37f-135">반면, 입력에 대해 처리할 수 있는 데이터가 구성 요소에 있는 경우 이 예는 입력 처리를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-135">Conversely, when the component still has data available to process for the input, the example suspends the processing of the input.</span></span> <span data-ttu-id="8b37f-136">이 예제에서는 `false` 해당 입력에 해당 하는 *canprocess* 배열의 요소 값을로 설정 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-136">The example does this by setting to `false` the value of the element in the *canProcess* array that corresponds to that input.</span></span>  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 <span data-ttu-id="8b37f-137">위의 예에서는 부울 `inputEOR` 배열을 사용하여 각 입력에 사용 가능한 추가 업스트림 데이터가 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-137">The preceding example uses the Boolean `inputEOR` array to indicate whether more upstream data is available for each input.</span></span> <span data-ttu-id="8b37f-138">이 배열 이름에서 `EOR`은 "행 집합의 끝(end of rowset)"을 나타내며 데이터 흐름 버퍼의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 속성을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-138">`EOR` in the name of the array represents "end of rowset" and refers to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property of data flow buffers.</span></span> <span data-ttu-id="8b37f-139">이 예에서 여기에 표시되지 않은 일부분인 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드는 받은 각 데이터 버퍼의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 속성 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-139">In a portion of the example that is not included here, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method checks the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property for each buffer of data that it receives.</span></span> <span data-ttu-id="8b37f-140">`true` 값이 입력에 사용할 수 있는 추가 업스트림 데이터가 없음을 나타내는 경우 이 예는 해당 입력에 대한 `inputEOR` 배열 요소 값을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-140">When a value of `true` indicates that there is no more upstream data available for an input, the example sets the value of the `inputEOR` array element for that input to `true`.</span></span> <span data-ttu-id="8b37f-141">이 메서드의 예제에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 배열 요소 값이 입력에 사용할 수 있는 업스트림 데이터가 없음을 나타내는 경우 *canprocess* 배열의 해당 요소 값을 `false` 입력에 대해로 설정 합니다 `inputEOR` .</span><span class="sxs-lookup"><span data-stu-id="8b37f-141">This example of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method sets the value of the corresponding element in the *canProcess* array to `false` for an input when the value of the `inputEOR` array element indicates that there is no more upstream data available for the input.</span></span>  
  
## <a name="implementing-the-getdependentinputs-method"></a><span data-ttu-id="8b37f-142">GetDependentInputs 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="8b37f-142">Implementing the GetDependentInputs Method</span></span>  
 <span data-ttu-id="8b37f-143">사용자 지정 데이터 흐름 구성 요소가 세 개 이상의 입력을 지원하는 경우에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드에 대한 구현도 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-143">When your custom data flow component supports more than two inputs, you must also provide an implementation for the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> class.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b37f-144"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드의 구현은 기본 클래스의 구현을 호출해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-144">Your implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method should not call the implementations in the base class.</span></span> <span data-ttu-id="8b37f-145">기본 클래스의 이 메서드에 대한 기본 구현은 `NotImplementedException`만 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-145">The default implementation of this method in the base class simply raises a `NotImplementedException`.</span></span>  
  
 <span data-ttu-id="8b37f-146">데이터 흐름 엔진은 사용자가 구성 요소에 세 개 이상의 입력을 연결한 경우에만 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-146">The data flow engine only calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method when the user attaches more than two inputs to the component.</span></span> <span data-ttu-id="8b37f-147">구성 요소에 입력이 두 개만 있고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 메서드가 하나의 입력이 차단 되었음을 나타내는 경우 (*canprocess*  =  `false` ) 데이터 흐름 엔진은 다른 입력이 추가 데이터를 받기 위해 대기 중인 것으로 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-147">When a component has only two inputs, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that one input is blocked (*canProcess* = `false`), the data flow engine knows that the other input is waiting to receive more data.</span></span> <span data-ttu-id="8b37f-148">그러나 입력이 세 개 이상일 때 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 메서드가 하나의 입력이 차단되었음을 나타내는 경우에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A>의 추가 코드가 추가 데이터를 받기 위해 대기 중인 입력을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-148">However, when there are more than two inputs, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> method indicates that one input is blocked, the additional code in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> identifies which inputs are waiting to receive more data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8b37f-149">사용자가 작성한 코드에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> 또는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드를 호출하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-149">You do not call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> methods in your own code.</span></span> <span data-ttu-id="8b37f-150">이러한 메서드와 사용자가 재정의한 `PipelineComponent` 클래스의 다른 메서드는 사용자의 구성 요소를 실행할 때 데이터 흐름 엔진에서 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-150">The data flow engine calls these methods, and the other methods of the `PipelineComponent` class that you override, when the data flow engine runs your component.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8b37f-151">예제</span><span class="sxs-lookup"><span data-stu-id="8b37f-151">Example</span></span>  
 <span data-ttu-id="8b37f-152">다음 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드의 구현은 차단된 특정 입력에 대해 추가 데이터를 받기 위해 대기 중이므로 지정된 입력을 차단하는 입력 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-152">For a specific input that is blocked, the following implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method returns a collection of the inputs that are waiting to receive more data, and are therefore blocking the specified input.</span></span> <span data-ttu-id="8b37f-153">구성 요소는 차단된 입력 외에 구성 요소에서 이미 받은 버퍼에 현재 처리할 수 있는 데이터가 없는(`inputBuffers[i].CurrentRow() == null`) 입력을 확인하는 방식으로 차단된 입력을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-153">The component identifies the blocking inputs by checking for inputs other than the blocked input that do not currently have data available to process in the buffers that the component has already received (`inputBuffers[i].CurrentRow() == null`).</span></span> <span data-ttu-id="8b37f-154">그런 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> 메서드에서 차단된 입력 컬렉션을 입력 ID 컬렉션으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8b37f-154">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> method then returns the collection of blocking inputs as a collection of input IDs.</span></span>  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  
