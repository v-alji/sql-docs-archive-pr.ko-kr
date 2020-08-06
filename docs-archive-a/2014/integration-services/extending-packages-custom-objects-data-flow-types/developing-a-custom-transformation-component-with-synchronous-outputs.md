---
title: 동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발 | Microsoft Docs
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
- ProcessInput method
- buffer allocations [Integration Services]
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- data flow components [Integration Services], transformation components
ms.assetid: b694d21f-9919-402d-9192-666c6449b0b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 94d78872570103d3df7e1cb96aecb144fafe4257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736615"
---
# <a name="developing-a-custom-transformation-component-with-synchronous-outputs"></a><span data-ttu-id="15685-102">동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="15685-102">Developing a Custom Transformation Component with Synchronous Outputs</span></span>
  <span data-ttu-id="15685-103">동기 출력을 사용하는 변환 구성 요소는 업스트림 구성 요소에서 행을 받고, 이러한 행을 다운스트림 구성 요소에 전달할 때 해당 행의 열 값을 읽거나 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-103">Transformation components with synchronous outputs receive rows from upstream components, and read or modify the values in the columns of these rows as they pass the rows to downstream components.</span></span> <span data-ttu-id="15685-104">또한 업스트림 구성 요소가 제공한 열에서 파생된 추가 출력 열도 정의할 수 있지만 데이터 흐름에 행을 추가하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-104">They may also define additional output columns that are derived from the columns provided by upstream components, but they do not add rows to the data flow.</span></span> <span data-ttu-id="15685-105">동기 구성 요소와 비동기 구성 요소 간의 차이점에 대한 자세한 내용은 [동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15685-105">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>  
  
 <span data-ttu-id="15685-106">이러한 종류의 구성 요소는 데이터가 구성 요소에 제공될 때 인라인으로 수정되는 태스크와 구성 요소에서 행을 처리하기 전에 모든 행을 볼 필요가 없는 태스크에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-106">This kind of component is suited for tasks where the data is modified inline as it is provided to the component and where the component does not have to see all the rows before processing them.</span></span> <span data-ttu-id="15685-107">동기 출력을 사용하는 변환은 일반적으로 외부 데이터 원본에 연결하거나 외부 메타데이터 열을 관리하거나 출력 버퍼에 행을 추가하지 않으므로 개발하기가 가장 쉬운 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="15685-107">It is the easiest component to develop because transformations with synchronous outputs typically do not connect to external data sources, manage external metadata columns, or add rows to output buffers.</span></span>  
  
 <span data-ttu-id="15685-108">동기 출력을 사용하는 변환 구성 요소를 만들려면 구성 요소에 대해 선택한 업스트림 열을 포함할 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>과 구성 요소에서 만드는 파생 열을 포함할 수 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 개체를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-108">Creating a transformation component with synchronous outputs involves adding an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> that will contain the upstream columns selected for the component, and a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that may contain derived columns created by the component.</span></span> <span data-ttu-id="15685-109">또한 디자인 타임 메서드를 구현하고, 실행 중 들어오는 버퍼 행의 열을 읽거나 수정하는 코드를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-109">It also includes implementing the design-time methods, and providing code that reads or modifies the columns in the incoming buffer rows during execution.</span></span>  
  
 <span data-ttu-id="15685-110">이 섹션에서는 사용자 지정 변환 구성 요소를 구현하는 데 필요한 정보를 제공하고 개념을 보다 쉽게 이해할 수 있도록 코드 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-110">This section provides the information that is required to implement a custom transformation component, and provides code examples to help you better understand the concepts.</span></span>  
  
## <a name="design-time"></a><span data-ttu-id="15685-111">디자인 타임</span><span class="sxs-lookup"><span data-stu-id="15685-111">Design Time</span></span>  
 <span data-ttu-id="15685-112">이 구성 요소의 디자인 타임 코드에서는 입력 및 출력을 만들고, 구성 요소에서 생성하는 다른 출력 열을 추가하고, 구성 요소의 구성에 대한 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-112">The design-time code for this component involves creating the inputs and outputs, adding any additional output columns that the component generates, and validating the configuration of the component.</span></span>  
  
### <a name="creating-the-component"></a><span data-ttu-id="15685-113">구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="15685-113">Creating the Component</span></span>  
 <span data-ttu-id="15685-114">구성 요소의 입력, 출력 및 사용자 지정 속성은 일반적으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 메서드 실행 중에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="15685-114">The inputs, outputs, and custom properties of the component are typically created during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="15685-115">동기 출력을 사용하는 변환 구성 요소의 입력 및 출력을 추가하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-115">There are two ways that you can add the input and the output of a transformation component with synchronous outputs.</span></span> <span data-ttu-id="15685-116">메서드의 기본 클래스 구현을 사용한 다음 만들어진 기본 입력 및 출력을 수정하거나, 개발자가 직접 입력 및 출력을 명시적으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-116">You can use the base class implementation of the method and then modify the default input and output that it creates, or you can explicitly add the input and output yourself.</span></span>  
  
 <span data-ttu-id="15685-117">다음 코드 예에서는 입력 및 출력 개체를 명시적으로 추가하는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15685-117">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that explicitly adds the input and output objects.</span></span> <span data-ttu-id="15685-118">동일한 동작을 수행하는 기본 클래스에 대한 호출은 주석에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-118">The call to the base class that would accomplish the same thing is included in a comment.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SynchronousComponent", ComponentType = ComponentType.Transform)]  
    public class SyncComponent : PipelineComponent  
    {  
  
        public override void ProvideComponentProperties()  
        {  
            // Add the input.  
            IDTSInput100 input = ComponentMetaData.InputCollection.New();  
            input.Name = "Input";  
  
            // Add the output.  
            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
            output.Name = "Output";  
            output.SynchronousInputID = input.ID;  
  
            // Alternatively, you can let the base class add the input and output  
            // and set the SynchronousInputID of the output to the ID of the input.  
            // base.ProvideComponentProperties();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsPipelineComponent(DisplayName:="SynchronousComponent", ComponentType:=ComponentType.Transform)> _  
Public Class SyncComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Add the input.  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()  
        input.Name = "Input"  
  
        ' Add the output.  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()  
        output.Name = "Output"  
        output.SynchronousInputID = Input.ID  
  
        ' Alternatively, you can let the base class add the input and output  
        ' and set the SynchronousInputID of the output to the ID of the input.  
        ' base.ProvideComponentProperties();  
  
    End Sub  
  
End Class  
```  
  
### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="15685-119">출력 열 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="15685-119">Creating and Configuring Output Columns</span></span>  
 <span data-ttu-id="15685-120">동기 출력을 사용하는 변환 구성 요소에서는 버퍼에 행을 추가하지는 않지만 다른 출력 열을 해당 출력에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-120">Although transformation components with synchronous outputs do not add rows to buffers, they may add extra output columns to their output.</span></span> <span data-ttu-id="15685-121">일반적으로 구성 요소에서 출력 열을 추가할 경우 새 출력 열의 값은 런타임에 업스트림 구성 요소에서 해당 구성 요소에 제공한 열 중 하나 이상의 열에 포함된 데이터로부터 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="15685-121">Typically, when a component adds an output column, the values for the new output column are derived at run time from the data that is contained in one or more of the columns provided to the component by an upstream component.</span></span>  
  
 <span data-ttu-id="15685-122">출력 열이 만들어진 후에는 해당 데이터 형식 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-122">After an output column has been created, its data type properties must be set.</span></span> <span data-ttu-id="15685-123">출력 열의 데이터 형식 속성을 설정하는 작업은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> 메서드 호출을 통해 수행되며 이 작업에는 특수한 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-123">Setting the data type properties of an output column requires special handling and is performed by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="15685-124"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> 속성은 각기 다른 속성의 설정에 따라 달라지기 때문에 개별적으로 읽기 전용이며 이 때문에 이 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-124">This method is required because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are individually read-only, because each depends on the settings of the other.</span></span> <span data-ttu-id="15685-125">이 메서드는 이러한 속성의 값이 일관성 있게 설정되도록 하며 데이터 흐름 태스크에서는 해당 값이 올바르게 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-125">This method guarantees that the values of the properties are set consistently, and the data flow task validates that they are set correctly.</span></span>  
  
 <span data-ttu-id="15685-126">열의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>은 다른 속성에 대해 설정되는 값을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-126">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="15685-127">다음 표에서는 각 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>의 종속 속성에 대한 요구 사항을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15685-127">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="15685-128">이 목록에 포함되지 않은 데이터 형식의 종속 속성은 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="15685-128">The data types not listed have their dependent properties set to zero.</span></span>  
  
|<span data-ttu-id="15685-129">DataType</span><span class="sxs-lookup"><span data-stu-id="15685-129">DataType</span></span>|<span data-ttu-id="15685-130">길이</span><span class="sxs-lookup"><span data-stu-id="15685-130">Length</span></span>|<span data-ttu-id="15685-131">확장</span><span class="sxs-lookup"><span data-stu-id="15685-131">Scale</span></span>|<span data-ttu-id="15685-132">자릿수</span><span class="sxs-lookup"><span data-stu-id="15685-132">Precision</span></span>|<span data-ttu-id="15685-133">CodePage</span><span class="sxs-lookup"><span data-stu-id="15685-133">CodePage</span></span>|  
|--------------|------------|-----------|---------------|--------------|  
|<span data-ttu-id="15685-134">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="15685-134">DT_DECIMAL</span></span>|<span data-ttu-id="15685-135">0</span><span class="sxs-lookup"><span data-stu-id="15685-135">0</span></span>|<span data-ttu-id="15685-136">0보다 크고 28보다 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-136">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="15685-137">0</span><span class="sxs-lookup"><span data-stu-id="15685-137">0</span></span>|<span data-ttu-id="15685-138">0</span><span class="sxs-lookup"><span data-stu-id="15685-138">0</span></span>|  
|<span data-ttu-id="15685-139">DT_CY</span><span class="sxs-lookup"><span data-stu-id="15685-139">DT_CY</span></span>|<span data-ttu-id="15685-140">0</span><span class="sxs-lookup"><span data-stu-id="15685-140">0</span></span>|<span data-ttu-id="15685-141">0</span><span class="sxs-lookup"><span data-stu-id="15685-141">0</span></span>|<span data-ttu-id="15685-142">0</span><span class="sxs-lookup"><span data-stu-id="15685-142">0</span></span>|<span data-ttu-id="15685-143">0</span><span class="sxs-lookup"><span data-stu-id="15685-143">0</span></span>|  
|<span data-ttu-id="15685-144">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="15685-144">DT_NUMERIC</span></span>|<span data-ttu-id="15685-145">0</span><span class="sxs-lookup"><span data-stu-id="15685-145">0</span></span>|<span data-ttu-id="15685-146">0보다 크고 28보다 작거나 같으며 Precision보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-146">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="15685-147">1보다 크거나 같고 38보다 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-147">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="15685-148">0</span><span class="sxs-lookup"><span data-stu-id="15685-148">0</span></span>|  
|<span data-ttu-id="15685-149">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="15685-149">DT_BYTES</span></span>|<span data-ttu-id="15685-150">0보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="15685-150">Greater than 0.</span></span>|<span data-ttu-id="15685-151">0</span><span class="sxs-lookup"><span data-stu-id="15685-151">0</span></span>|<span data-ttu-id="15685-152">0</span><span class="sxs-lookup"><span data-stu-id="15685-152">0</span></span>|<span data-ttu-id="15685-153">0</span><span class="sxs-lookup"><span data-stu-id="15685-153">0</span></span>|  
|<span data-ttu-id="15685-154">DT_STR</span><span class="sxs-lookup"><span data-stu-id="15685-154">DT_STR</span></span>|<span data-ttu-id="15685-155">0보다 크고 8000보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-155">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="15685-156">0</span><span class="sxs-lookup"><span data-stu-id="15685-156">0</span></span>|<span data-ttu-id="15685-157">0</span><span class="sxs-lookup"><span data-stu-id="15685-157">0</span></span>|<span data-ttu-id="15685-158">0이 아니며 올바른 코드 페이지가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="15685-158">Not 0, and a valid code page.</span></span>|  
|<span data-ttu-id="15685-159">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="15685-159">DT_WSTR</span></span>|<span data-ttu-id="15685-160">0보다 크고 4000보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-160">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="15685-161">0</span><span class="sxs-lookup"><span data-stu-id="15685-161">0</span></span>|<span data-ttu-id="15685-162">0</span><span class="sxs-lookup"><span data-stu-id="15685-162">0</span></span>|<span data-ttu-id="15685-163">0</span><span class="sxs-lookup"><span data-stu-id="15685-163">0</span></span>|  
  
 <span data-ttu-id="15685-164">데이터 형식 속성에 대한 제한 사항은 출력 열의 데이터 형식을 기준으로 하므로 관리되는 형식을 사용할 때는 올바른 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-164">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="15685-165">기본 클래스에서는 관리되는 구성 요소 개발자가 관리되는 형식의 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식을 선택하는 데 도움이 되는 세 개의 도우미 메서드 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-165">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> that assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="15685-166">이러한 메서드는 관리되는 데이터 형식을 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식으로 변환하거나 그 반대로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-166">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>  
  
## <a name="run-time"></a><span data-ttu-id="15685-167">런타임</span><span class="sxs-lookup"><span data-stu-id="15685-167">Run Time</span></span>  
 <span data-ttu-id="15685-168">일반적으로 구성 요소의 런타임 부분에 대한 구현은 버퍼에서 구성 요소의 입력 및 출력 열을 찾는 태스크와 들어오는 버퍼 행에서 이러한 열의 값을 읽거나 쓰는 태스크로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="15685-168">Generally, the implementation of the run-time part of the component is categorized into two tasks-locating the input and output columns of the component in the buffer, and reading or writing the values of these columns in the incoming buffer rows.</span></span>  
  
### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="15685-169">버퍼에서 열 찾기</span><span class="sxs-lookup"><span data-stu-id="15685-169">Locating Columns in the Buffer</span></span>  
 <span data-ttu-id="15685-170">실행 중 구성 요소에 제공되는 버퍼의 열 수는 구성 요소의 입력 또는 출력 컬렉션에 있는 열 수를 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-170">The number of columns in the buffers that are provided to a component during execution will likely exceed the number of columns in the input or output collections of the component.</span></span> <span data-ttu-id="15685-171">이는 각 버퍼에 데이터 흐름의 구성 요소에 정의된 출력 열이 모두 들어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="15685-171">This is because each buffer contains all the output columns defined in the components in a data flow.</span></span> <span data-ttu-id="15685-172">버퍼의 열 수가 입력 또는 출력의 열 수와 정확하게 일치하도록 하려면 구성 요소 개발자가 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-172">To ensure that the buffer columns are correctly matched to the columns of the input or output, component developers must use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="15685-173">이 메서드는 지정된 버퍼에서 열의 계보 ID로 열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-173">This method locates a column in the specified buffer by its lineage ID.</span></span> <span data-ttu-id="15685-174">런타임에 처음으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 속성을 사용할 수 있게 되는 메서드는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>이므로 일반적으로 이 메서드가 실행될 때 열을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-174">Typically columns are located during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> because this is the first run-time method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property becomes available.</span></span>  
  
 <span data-ttu-id="15685-175">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 실행 중 입력 및 출력 열 컬렉션에서 열의 인덱스를 찾는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15685-175">The following code example shows a component that locates indexes of the columns in its input and output column collection during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span> <span data-ttu-id="15685-176">열 인덱스는 정수 배열에 저장되며 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 실행 중 열 인덱스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-176">The column indexes are stored in an integer array, and can be accessed by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
```csharp  
int []inputColumns;  
int []outputColumns;  
  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    inputColumns = new int[input.InputColumnCollection.Count];  
    outputColumns = new int[output.OutputColumnCollection.Count];  
  
    for(int col=0; col < input.InputColumnCollection.Count; col++)  
    {  
        IDTSInputColumn100 inputColumn = input.InputColumnCollection[col];  
        inputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID);  
    }  
  
    for(int col=0; col < output.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 outputColumn = output.OutputColumnCollection[col];  
        outputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID);  
    }  
  
}  
```  
  
```vb  
Public Overrides Sub PreExecute()  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    ReDim inputColumns(input.InputColumnCollection.Count)  
    ReDim outputColumns(output.OutputColumnCollection.Count)  
  
    For col As Integer = 0 To input.InputColumnCollection.Count  
  
        Dim inputColumn As IDTSInputColumn100 = input.InputColumnCollection(col)  
        inputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID)  
    Next  
  
    For col As Integer = 0 To output.OutputColumnCollection.Count  
  
        Dim outputColumn As IDTSOutputColumn100 = output.OutputColumnCollection(col)  
        outputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID)  
    Next  
  
End Sub  
```  
  
### <a name="processing-rows"></a><span data-ttu-id="15685-177">행 처리</span><span class="sxs-lookup"><span data-stu-id="15685-177">Processing Rows</span></span>  
 <span data-ttu-id="15685-178">구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 메서드에서 행 및 열이 들어 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 개체를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-178">Components receive <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain rows and columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="15685-179">이 메서드가 실행되는 동안에는 버퍼의 행을 반복하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 실행 중 식별된 열을 읽고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-179">During this method the rows in the buffer are iterated, and the columns identified during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> are read and modified.</span></span> <span data-ttu-id="15685-180">이 메서드는 업스트림 구성 요소에서 더 이상 행을 제공하지 않을 때까지 데이터 흐름 태스크에서 반복적으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="15685-180">The method is called repeatedly by the data flow task until no more rows are provided from the upstream component.</span></span>  
  
 <span data-ttu-id="15685-181">버퍼의 개별 열은 배열 인덱서 액세스 메서드를 사용하거나 `Get` 또는 `Set` 메서드 중 하나를 사용하여 읽거나 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-181">An individual column in the buffer is read or written by using the array indexer access method, or by using one of the `Get` or `Set` methods.</span></span> <span data-ttu-id="15685-182">`Get` 및 `Set` 메서드가 보다 효율적이므로 버퍼에 있는 열의 데이터 형식을 알고 있는 경우에는 이 두 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15685-182">The `Get` and `Set` methods are more efficient and should be used when the data type of the column in the buffer is known.</span></span>  
  
 <span data-ttu-id="15685-183">다음 코드 예에서는 들어오는 행을 처리하는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 메서드의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15685-183">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method that processes incoming rows.</span></span>  
  
```csharp  
public override void ProcessInput( int InputID, PipelineBuffer buffer)  
{  
       while( buffer.NextRow())  
       {  
            for(int x=0; x < inputColumns.Length;x++)  
            {  
                if(!buffer.IsNull(inputColumns[x]))  
                {  
                    object columnData = buffer[inputColumns[x]];  
                    // TODO: Modify the column data.  
                    buffer[inputColumns[x]] = columnData;  
                }  
            }  
  
      }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal InputID As Integer, ByVal buffer As PipelineBuffer)  
  
        While (buffer.NextRow())  
  
            For x As Integer = 0 To inputColumns.Length  
  
                if buffer.IsNull(inputColumns(x)) = false then  
  
                    Dim columnData As Object = buffer(inputColumns(x))  
                    ' TODO: Modify the column data.  
                    buffer(inputColumns(x)) = columnData  
  
                End If  
            Next  
  
        End While  
End Sub  
```  
  
## <a name="sample"></a><span data-ttu-id="15685-184">샘플</span><span class="sxs-lookup"><span data-stu-id="15685-184">Sample</span></span>  
 <span data-ttu-id="15685-185">다음 예제에서는 동기 출력을 사용하며 모든 문자열 열의 값을 대문자로 변환하는 간단한 변환 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15685-185">The following sample shows a simple transformation component with synchronous outputs that converts the values of all string columns to uppercase.</span></span> <span data-ttu-id="15685-186">이 예제는 이 항목에 설명된 메서드 및 기능의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15685-186">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="15685-187">여기에서는 동기 출력을 사용하는 모든 사용자 지정 변환 구성 요소에서 재정의해야 하는 중요한 메서드를 보여 주지만 디자인 타임 유효성 검사를 위한 코드는 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15685-187">It demonstrates the important methods that every custom transformation component with synchronous outputs must override, but does not contain code for design-time validation.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace Uppercase  
{  
  [DtsPipelineComponent(DisplayName = "Uppercase")]  
  public class Uppercase : PipelineComponent  
  {  
    ArrayList m_ColumnIndexList = new ArrayList();  
  
    public override void ProvideComponentProperties()  
    {  
      base.ProvideComponentProperties();  
      ComponentMetaData.InputCollection[0].Name = "Uppercase Input";  
      ComponentMetaData.OutputCollection[0].Name = "Uppercase Output";  
    }  
  
    public override void PreExecute()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection[0];  
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;  
  
      foreach (IDTSInputColumn100 column in inputColumns)  
      {  
        if (column.DataType == DataType.DT_STR || column.DataType == DataType.DT_WSTR)  
        {  
          m_ColumnIndexList.Add((int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID));  
        }  
      }  
    }  
  
    public override void ProcessInput(int inputID, PipelineBuffer buffer)  
    {  
      while (buffer.NextRow())  
      {  
        foreach (int columnIndex in m_ColumnIndexList)  
        {  
          string str = buffer.GetString(columnIndex);  
          buffer.SetString(columnIndex, str.ToUpper());  
        }  
      }  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.Collections   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper   
Namespace Uppercase   
  
 <DtsPipelineComponent(DisplayName="Uppercase")> _   
 Public Class Uppercase   
 Inherits PipelineComponent   
   Private m_ColumnIndexList As ArrayList = New ArrayList   
  
   Public  Overrides Sub ProvideComponentProperties()   
     MyBase.ProvideComponentProperties   
     ComponentMetaData.InputCollection(0).Name = "Uppercase Input"   
     ComponentMetaData.OutputCollection(0).Name = "Uppercase Output"   
   End Sub   
  
   Public  Overrides Sub PreExecute()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection   
     For Each column As IDTSInputColumn100 In inputColumns   
       If column.DataType = DataType.DT_STR OrElse column.DataType = DataType.DT_WSTR Then   
         m_ColumnIndexList.Add(CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer))   
       End If   
     Next   
   End Sub   
  
   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
     While buffer.NextRow   
       For Each columnIndex As Integer In m_ColumnIndexList   
         Dim str As String = buffer.GetString(columnIndex)   
         buffer.SetString(columnIndex, str.ToUpper)   
       Next   
     End While   
   End Sub   
 End Class   
End Namespace  
```  
  
<span data-ttu-id="15685-188">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="15685-188">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="15685-189">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="15685-189">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="15685-190">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="15685-190">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="15685-191">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="15685-191">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15685-192">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15685-192">See Also</span></span>  
 <span data-ttu-id="15685-193">[비동기 출력을 사용 하 여 사용자 지정 변환 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span><span class="sxs-lookup"><span data-stu-id="15685-193">[Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span></span>  
 <span data-ttu-id="15685-194">[동기 및 비동기 변환 이해](../understanding-synchronous-and-asynchronous-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="15685-194">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) </span></span>  
 [<span data-ttu-id="15685-195">스크립트 구성 요소를 사용하여 동기 변환 만들기</span><span class="sxs-lookup"><span data-stu-id="15685-195">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
