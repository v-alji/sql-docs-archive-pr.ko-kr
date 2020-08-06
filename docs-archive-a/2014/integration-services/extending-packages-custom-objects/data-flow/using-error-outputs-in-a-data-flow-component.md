---
title: 데이터 흐름 구성 요소에서 오류 출력 사용 | Microsoft Docs
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
- errors [Integration Services], alternative outputs
- synchronous error outputs [Integration Services]
- alternative error outputs [Integration Services]
- custom data flow components [Integration Services], error outputs
- data flow components [Integration Services], error outputs
- populating error columns [Integration Services]
- redirecting error output [Integration Services]
- error outputs [Integration Services]
- asynchronous error outputs [Integration Services]
ms.assetid: a2a3e7c8-1de2-45b3-97fb-60415d3b0934
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a05a41065c52fadbe7f7fc065771727310e58149
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638909"
---
# <a name="using-error-outputs-in-a-data-flow-component"></a><span data-ttu-id="50247-102">데이터 흐름 구성 요소에서 오류 출력 사용</span><span class="sxs-lookup"><span data-stu-id="50247-102">Using Error Outputs in a Data Flow Component</span></span>
  <span data-ttu-id="50247-103">구성 요소에 오류 출력이라는 특수한 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 개체를 추가하면 실행 중 해당 구성 요소에서 처리할 수 없는 행을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-103">Special <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> objects called error outputs can be added to components to let the component redirect rows that it cannot process during execution.</span></span> <span data-ttu-id="50247-104">구성 요소에서 발생할 수 있는 문제는 일반적으로 오류 또는 잘림으로 분류되며 각 구성 요소와만 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-104">The problems a component may encounter are generally categorized as errors or truncations, and are specific to each component.</span></span> <span data-ttu-id="50247-105">구성 요소에서 오류 출력을 제공할 경우 해당 구성 요소의 사용자는 결과 집합에서 오류 행을 필터링하거나, 문제가 발생할 때 해당 구성 요소를 실패로 처리하거나, 오류를 무시하고 계속하는 방법으로 유연하게 오류 조건을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-105">Components that provide error outputs give users of the component the flexibility to handle error conditions by filtering error rows out of the result set, by failing the component when a problem occurs, or by ignoring errors and continuing.</span></span>  
  
 <span data-ttu-id="50247-106">구성 요소에서 오류 출력을 구현 및 지원하려면 먼저 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.UsesDispositions%2A> 속성을 `true`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-106">To implement and support error outputs in a component, you must first set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.UsesDispositions%2A> property of the component to `true`.</span></span> <span data-ttu-id="50247-107">그런 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> 속성이 `true`로 설정된 구성 요소에 출력을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-107">Then you must add an output to the component that has its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> property set to `true`.</span></span> <span data-ttu-id="50247-108">마지막으로, 오류 또는 잘림이 발생할 경우 오류 출력으로 행을 리디렉션하는 코드를 구성 요소에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-108">Finally, the component must contain code that redirects rows to the error output when errors or truncations occur.</span></span> <span data-ttu-id="50247-109">이 항목에서는 이러한 세 단계를 설명하고 동기 오류 출력과 비동기 오류 출력의 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-109">This topic covers these three steps and explains the differences between synchronous and asynchronous error outputs.</span></span>  
  
## <a name="creating-an-error-output"></a><span data-ttu-id="50247-110">오류 출력 만들기</span><span class="sxs-lookup"><span data-stu-id="50247-110">Creating an Error Output</span></span>  
 <span data-ttu-id="50247-111">오류 출력을 만들려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100.New%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.OutputCollection%2A> 메서드를 호출한 다음 새 출력의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-111">You create an error output by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100.New%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.OutputCollection%2A>, and then setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.IsErrorOut%2A> property of the new output to `true`.</span></span> <span data-ttu-id="50247-112">출력이 비동기적인 경우에는 출력에 대해 아무 작업도 수행하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-112">If the output is asynchronous, nothing else must be done to the output.</span></span> <span data-ttu-id="50247-113">출력이 동기적이고 동일한 입력에 대해 동기적인 다른 출력이 더 있는 경우에는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExclusionGroup%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 속성도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-113">If the output is synchronous, and there is another output that is synchronous to the same input, you must also set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExclusionGroup%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> properties.</span></span> <span data-ttu-id="50247-114">두 속성은 모두 동일한 입력에 대해 동기적인 다른 출력과 동일한 값으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-114">Both properties should have the same values as the other output that is synchronous to the same input.</span></span> <span data-ttu-id="50247-115">이러한 속성이 0이 아닌 값으로 설정되어 있는 경우 입력에서 제공된 행은 해당 입력에 동기적인 두 출력 모두로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="50247-115">If these properties are not set to a non-zero value, the rows provided by the input are sent to both outputs that are synchronous to the input.</span></span>  
  
 <span data-ttu-id="50247-116">실행 중 구성 요소에서 오류나 잘림이 발생할 경우에는 오류가 발생한 입력/출력 또는 입력/출력 열의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ErrorRowDisposition%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.TruncationRowDisposition%2A> 속성 설정에 따라 진행 방식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50247-116">When a component encounters an error or truncation during execution, it proceeds based on the settings of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ErrorRowDisposition%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.TruncationRowDisposition%2A> properties of the input or output, or input or output column, where the error occurred.</span></span> <span data-ttu-id="50247-117">이러한 속성 값은 기본적으로 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition.RD_NotUsed>로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50247-117">The value of these properties should be set by default to <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition.RD_NotUsed>.</span></span> <span data-ttu-id="50247-118">구성 요소의 오류 출력이 다운스트림 구성 요소에 연결된 경우 이 속성은 구성 요소 사용자가 설정하며 사용자는 이 속성을 통해 구성 요소에서 오류 또는 잘림을 처리하는 방식을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-118">When the error output of the component is connected to a downstream component, this property is set by the user of the component and lets the user control how the component handles the error or truncation.</span></span>  
  
## <a name="populating-error-columns"></a><span data-ttu-id="50247-119">오류 열 채우기</span><span class="sxs-lookup"><span data-stu-id="50247-119">Populating Error Columns</span></span>  
 <span data-ttu-id="50247-120">오류 출력이 만들어지면 데이터 흐름 태스크에서는 출력 열 컬렉션에 두 개의 열을 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-120">When an error output is created, the data flow task automatically adds two columns to the output column collection.</span></span> <span data-ttu-id="50247-121">이러한 열은 구성 요소에서 오류 또는 잘림을 발생시킨 열의 ID를 지정하고 구성 요소별 오류 코드를 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="50247-121">These columns are used by components to specify the ID of the column that caused the error or truncation, and to provide the component-specific error code.</span></span> <span data-ttu-id="50247-122">이러한 열은 자동으로 생성되지만 열에 포함되는 값은 구성 요소에서 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-122">These columns are generated automatically, but the values contained in the columns must be set by the component.</span></span>  
  
 <span data-ttu-id="50247-123">이러한 열의 값을 설정하는 데 사용되는 메서드는 오류 출력이 동기적인지 비동기적인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="50247-123">The method used to set the values of these columns depends on whether the error output is synchronous or asynchronous.</span></span> <span data-ttu-id="50247-124">동기 출력을 사용하는 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> 메서드를 호출하고(자세한 내용은 다음 섹션 참조) 오류 코드 및 오류 열 값을 매개 변수로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-124">Components with synchronous outputs call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> method, discussed in more detail in the next section, and provide the error code and error column values as parameters.</span></span> <span data-ttu-id="50247-125">비동기 출력을 사용하는 구성 요소에서는 두 가지 방법 중 하나로 이러한 열의 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-125">Components with asynchronous outputs have two choices for setting the values of these columns.</span></span> <span data-ttu-id="50247-126">출력 버퍼의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 메서드를 호출하고 값을 지정하거나, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A>를 사용하여 버퍼에서 오류 열을 찾고 해당 열의 값을 직접 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-126">They can either call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method of the output buffer and supply the values, or locate the error columns in the buffer by using <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> and set the values for the columns directly.</span></span> <span data-ttu-id="50247-127">하지만 열 이름이 변경되거나 출력 열 컬렉션에서의 열 위치가 수정된 경우도 있을 수 있으므로 두 번째 방법은 안정적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-127">However, because the names of the columns may have been changed, or their location in the output column collection may have been modified, the latter method may not be reliable.</span></span> <span data-ttu-id="50247-128"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 메서드는 이러한 오류 열의 값을 자동으로 설정하므로 오류 열을 수동으로 찾을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-128">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method automatically sets the values in these error columns without having to locate them manually.</span></span>  
  
 <span data-ttu-id="50247-129">특정 오류 코드에 해당하는 오류 설명을 가져와야 하는 경우 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> 속성을 통해 사용할 수 있는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-129">If you need to obtain the error description that corresponds to a specific error code, you can use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the component's <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span>  
  
 <span data-ttu-id="50247-130">다음 코드 예에서는 하나의 입력과 오류 출력을 포함한 두 개의 출력을 사용하는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50247-130">The following code examples show a component that has an input and two outputs, including an error output.</span></span> <span data-ttu-id="50247-131">첫 번째 예에서는 입력에 동기적인 오류 출력을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50247-131">The first example shows how to create an error output that is synchronous to the input.</span></span> <span data-ttu-id="50247-132">두 번째 예에서는 비동기적인 오류 출력을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50247-132">The second example shows how to create an error output that is asynchronous.</span></span>  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    // Specify that the component has an error output.  
    ComponentMetaData.UsesDispositions = true;  
    // Create the input.  
    IDTSInput100 input = ComponentMetaData.InputCollection.New();  
    input.Name = "Input";  
    input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed;  
    input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution.";  
  
    // Create the default output.  
    IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
    output.Name = "Output";  
    output.SynchronousInputID = input.ID;  
    output.ExclusionGroup = 1;  
  
    // Create the error output.  
    IDTSOutput100 errorOutput = ComponentMetaData.OutputCollection.New();  
    errorOutput.IsErrorOut = true;  
    errorOutput.Name = "ErrorOutput";  
    errorOutput.SynchronousInputID = input.ID;  
    errorOutput.ExclusionGroup = 1;  
  
}  
```  
  
```vb  
Public  Overrides Sub ProvideComponentProperties()   
  
 ' Specify that the component has an error output.  
 ComponentMetaData.UsesDispositions = True   
  
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New   
  
 ' Create the input.  
 input.Name = "Input"   
 input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed   
 input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution."   
  
 ' Create the default output.  
 Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 output.Name = "Output"   
 output.SynchronousInputID = input.ID   
 output.ExclusionGroup = 1   
  
 ' Create the error output.  
 Dim errorOutput As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 errorOutput.IsErrorOut = True   
 errorOutput.Name = "ErrorOutput"   
 errorOutput.SynchronousInputID = input.ID   
 errorOutput.ExclusionGroup = 1   
  
End Sub  
```  
  
 <span data-ttu-id="50247-133">다음 코드 예에서는 비동기적인 오류 출력을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50247-133">The following code example creates an error output that is asynchronous.</span></span>  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    // Specify that the component has an error output.  
    ComponentMetaData.UsesDispositions = true;  
  
    // Create the input.  
    IDTSInput100 input = ComponentMetaData.InputCollection.New();  
    input.Name = "Input";  
    input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed;  
    input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution.";  
  
    // Create the default output.  
    IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
    output.Name = "Output";  
  
    // Create the error output.  
    IDTSOutput100 errorOutput = ComponentMetaData.OutputCollection.New();  
    errorOutput.Name = "ErrorOutput";  
    errorOutput.IsErrorOut = true;  
}  
```  
  
```vb  
Public  Overrides Sub ProvideComponentProperties()   
  
 ' Specify that the component has an error output.  
 ComponentMetaData.UsesDispositions = True   
  
 ' Create the input.  
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New   
  
 ' Create the default output.  
 input.Name = "Input"   
 input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed   
 input.ErrorOrTruncationOperation = "A string describing the possible error or truncation that may occur during execution."   
  
 ' Create the error output.  
 Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 output.Name = "Output"   
 Dim errorOutput As IDTSOutput100 = ComponentMetaData.OutputCollection.New   
 errorOutput.Name = "ErrorOutput"   
 errorOutput.IsErrorOut = True   
  
End Sub  
```  
  
## <a name="redirecting-a-row-to-an-error-output"></a><span data-ttu-id="50247-134">행을 오류 출력으로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="50247-134">Redirecting a Row to an Error Output</span></span>  
 <span data-ttu-id="50247-135">구성 요소에 오류 출력을 추가한 후에는 해당 구성 요소와 관련된 오류 또는 잘림 조건을 처리하고 해당 오류 또는 잘림 행을 오류 출력으로 리디렉션하는 코드를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-135">After adding an error output to a component, you must provide code that handles the error or truncation conditions specific to the component and redirects the error or truncation rows to the error output.</span></span> <span data-ttu-id="50247-136">이 작업은 오류 출력이 동기적인지 비동기적인지에 따라 두 가지 방법 중 하나로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-136">You can do this in two ways, depending on whether the error output is synchronous or asynchronous.</span></span>  
  
### <a name="redirecting-a-row-with-synchronous-outputs"></a><span data-ttu-id="50247-137">동기 출력을 사용하는 경우 행 리디렉션</span><span class="sxs-lookup"><span data-stu-id="50247-137">Redirecting a Row with Synchronous Outputs</span></span>  
 <span data-ttu-id="50247-138"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 메서드를 호출하면 행이 동기 출력으로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="50247-138">Rows are sent to synchronous outputs by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> class.</span></span> <span data-ttu-id="50247-139">이 메서드를 호출할 때는 오류 출력의 ID, 구성 요소에 정의된 오류 코드 및 구성 요소에서 처리하지 못한 열의 인덱스를 매개 변수로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-139">The method call includes as parameters the ID of the error output, the component-defined error code, and the index of the column that the component was unable to process.</span></span>  
  
 <span data-ttu-id="50247-140">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> 메서드를 사용하여 버퍼의 행을 동기 오류 출력으로 전송하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50247-140">The following code example demonstrates how to direct a row in a buffer to a synchronous error output using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.DirectErrorRow%2A> method.</span></span>  
  
```csharp  
public override void ProcessInput(int inputID, PipelineBuffer buffer)  
{  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
  
        // This code sample assumes the component has two outputs, one the default,  
        // the other the error output. If the errorOutputIndex returned from GetErrorOutputInfo  
        // is 0, then the default output is the second output in the collection.  
        int defaultOutputID = -1;  
        int errorOutputID = -1;  
        int errorOutputIndex = -1;  
  
        GetErrorOutputInfo(ref errorOutputID,ref errorOutputIndex);  
  
        if (errorOutputIndex == 0)  
            defaultOutputID = ComponentMetaData.OutputCollection[1].ID;  
        else  
            defaultOutputID = ComponentMetaData.OutputCollection[0].ID;  
  
        while (buffer.NextRow())  
        {  
            try  
            {  
                // TODO: Implement code to process the columns in the buffer row.  
  
                // Ideally, your code should detect potential exceptions before they occur, rather  
                // than having a generic try/catch block such as this.   
                // However, because the error or truncation implementation is specific to each component,  
                // this sample focuses on actually directing the row, and not a single error or truncation.  
  
                // Unless an exception occurs, direct the row to the default   
                buffer.DirectRow(defaultOutputID);  
            }  
            catch  
            {  
                // Yes, has the user specified to redirect the row?  
                if (input.ErrorRowDisposition == DTSRowDisposition.RD_RedirectRow)  
                {  
                    // Yes, direct the row to the error output.  
                    // TODO: Add code to include the errorColumnIndex.  
                    buffer.DirectErrorRow(errorOutputID, 0, errorColumnIndex);  
                }  
                else if (input.ErrorRowDisposition == DTSRowDisposition.RD_FailComponent || input.ErrorRowDisposition == DTSRowDisposition.RD_NotUsed)  
                {  
                    // No, the user specified to fail the component, or the error row disposition was not set.  
                    throw new Exception("An error occurred, and the DTSRowDisposition is either not set, or is set to fail component.");  
                }  
                else  
                {  
                    // No, the user specified to ignore the failure so   
                    // direct the row to the default output.  
                    buffer.DirectRow(defaultOutputID);  
                }  
  
            }  
        }  
}  
```  
  
```vb  
Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
   Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)   
  
   ' This code sample assumes the component has two outputs, one the default,  
   ' the other the error output. If the errorOutputIndex returned from GetErrorOutputInfo  
   ' is 0, then the default output is the second output in the collection.  
   Dim defaultOutputID As Integer = -1   
   Dim errorOutputID As Integer = -1   
   Dim errorOutputIndex As Integer = -1   
  
   GetErrorOutputInfo(errorOutputID, errorOutputIndex)   
  
   If errorOutputIndex = 0 Then   
     defaultOutputID = ComponentMetaData.OutputCollection(1).ID   
   Else   
     defaultOutputID = ComponentMetaData.OutputCollection(0).ID   
   End If   
  
   While buffer.NextRow   
     Try   
       ' TODO: Implement code to process the columns in the buffer row.  
  
       ' Ideally, your code should detect potential exceptions before they occur, rather  
       ' than having a generic try/catch block such as this.   
       ' However, because the error or truncation implementation is specific to each component,  
       ' this sample focuses on actually directing the row, and not a single error or truncation.  
  
       ' Unless an exception occurs, direct the row to the default   
       buffer.DirectRow(defaultOutputID)   
     Catch   
       ' Yes, has the user specified to redirect the row?  
       If input.ErrorRowDisposition = DTSRowDisposition.RD_RedirectRow Then   
         ' Yes, direct the row to the error output.  
         ' TODO: Add code to include the errorColumnIndex.  
         buffer.DirectErrorRow(errorOutputID, 0, errorColumnIndex)   
       Else   
         If input.ErrorRowDisposition = DTSRowDisposition.RD_FailComponent OrElse input.ErrorRowDisposition = DTSRowDisposition.RD_NotUsed Then   
           ' No, the user specified to fail the component, or the error row disposition was not set.  
           Throw New Exception("An error occurred, and the DTSRowDisposition is either not set, or is set to fail component.")   
         Else   
           ' No, the user specified to ignore the failure so   
           ' direct the row to the default output.  
           buffer.DirectRow(defaultOutputID)   
         End If   
       End If   
     End Try   
   End While   
End Sub  
```  
  
### <a name="redirecting-a-row-with-asynchronous-outputs"></a><span data-ttu-id="50247-141">비동기 출력을 사용하는 경우 행 리디렉션</span><span class="sxs-lookup"><span data-stu-id="50247-141">Redirecting a Row with Asynchronous Outputs</span></span>  
 <span data-ttu-id="50247-142">비동기 출력을 사용하는 구성 요소에서는 동기 오류 출력을 사용할 때와 같이 행을 출력으로 전송하는 대신 출력 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>에 행을 명시적으로 추가하여 행을 오류 출력으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="50247-142">Instead of directing rows to an output, as is done with synchronous error outputs, components with asynchronous outputs send a row to an error output by explicitly adding a row to the output <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>.</span></span> <span data-ttu-id="50247-143">비동기 오류 출력을 사용하는 구성 요소를 구현하려면 다운스트림 구성 요소에 제공된 오류 출력에 열을 추가하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드 실행 중 구성 요소에 제공된 오류 출력에 대한 출력 버퍼를 캐시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-143">Implementing a component that uses asynchronous error outputs requires adding columns to the error output that are provided to downstream components, and caching the output buffer for the error output that is provided to the component during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="50247-144">비동기 출력을 사용하는 구성 요소 구현에 대한 세부 정보는 [비동기 출력을 사용하여 사용자 지정 변환 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) 항목에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-144">The details of implementing a component with asynchronous outputs are covered in detail in the topic [Developing a Custom Transformation Component with Asynchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).</span></span> <span data-ttu-id="50247-145">오류 출력에 열이 명시적으로 추가되지 않을 경우 출력 버퍼에 추가된 버퍼 행에는 두 개의 오류 열만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50247-145">If columns are not explicitly added to the error output, the buffer row that is added to the output buffer contains only the two error columns.</span></span>  
  
 <span data-ttu-id="50247-146">행을 비동기 오류 출력으로 보내려면 오류 출력 버퍼에 행을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-146">To send a row to an asynchronous error output, you must add a row to the error output buffer.</span></span> <span data-ttu-id="50247-147">일부 경우에는 행이 이미 오류가 아닌 출력 버퍼에 추가되어 있을 수 있으며 이 경우 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RemoveRow%2A> 메서드를 사용하여 해당 행을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-147">Sometimes, a row may have already been added to the non-error output buffer and you must remove this row by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RemoveRow%2A> method.</span></span> <span data-ttu-id="50247-148">그런 다음 출력 버퍼의 열 값을 설정하고, 마지막으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 메서드를 호출하여 구성 요소별 오류 코드와 오류 열 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-148">Next you set the output buffer columns values, and finally, you call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method to provide the component-specific error code and the error column value.</span></span>  
  
 <span data-ttu-id="50247-149">다음 예에서는 비동기 출력을 사용하는 구성 요소에 대해 오류 출력을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50247-149">The following example demonstrates how to use an error output for a component with asynchronous outputs.</span></span> <span data-ttu-id="50247-150">시뮬레이션된 오류가 발생하면 해당 구성 요소에서는 오류 출력 버퍼에 행을 추가하고, 이전에 오류가 아닌 출력 버퍼에 추가된 값을 오류 출력 버퍼에 복사하고, 오류가 아닌 출력 버퍼에 추가된 행을 제거한 다음, 마지막으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> 메서드를 호출하여 오류 코드와 오류 열 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50247-150">When the simulated error occurs, the component adds a row to the error output buffer, copies the values that were previously added to the non-error output buffer to the error output buffer, removes the row that was added to the non-error output buffer, and, finally, sets the error code and error column values by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetErrorInfo%2A> method.</span></span>  
  
```csharp  
int []columnIndex;  
int errorOutputID = -1;  
int errorOutputIndex = -1;  
  
public override void PreExecute()  
{  
    IDTSOutput100 defaultOutput = null;  
  
    this.GetErrorOutputInfo(ref errorOutputID, ref errorOutputIndex);  
    foreach (IDTSOutput100 output in ComponentMetaData.OutputCollection)  
    {  
        if (output.ID != errorOutputID)  
            defaultOutput = output;  
    }  
  
    columnIndex = new int[defaultOutput.OutputColumnCollection.Count];  
  
    for(int col =0 ; col < defaultOutput.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 column = defaultOutput.OutputColumnCollection[col];  
        columnIndex[col] = BufferManager.FindColumnByLineageID(defaultOutput.Buffer, column.LineageID);  
    }  
}  
  
public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        if (outputIDs[x] == errorOutputID)  
            this.errorBuffer = buffers[x];  
        else  
            this.defaultBuffer = buffers[x];  
    }  
  
    int rows = 100;  
  
    Random random = new Random(System.DateTime.Now.Millisecond);  
  
    for (int row = 0; row < rows; row++)  
    {  
        try  
        {  
            defaultBuffer.AddRow();  
  
            for (int x = 0; x < columnIndex.Length; x++)  
                defaultBuffer[columnIndex[x]] = random.Next();  
  
            // Simulate an error.  
            if ((row % 2) == 0)  
                throw new Exception("A simulated error.");  
        }  
        catch  
        {  
            // Add a row to the error buffer.  
            errorBuffer.AddRow();  
  
            // Get the values from the default buffer  
            // and copy them to the error buffer.  
            for (int x = 0; x < columnIndex.Length; x++)  
                errorBuffer[columnIndex[x]] = defaultBuffer[columnIndex[x]];  
  
            // Set the error information.  
            errorBuffer.SetErrorInfo(errorOutputID, 1, 0);  
  
            // Remove the row that was added to the default buffer.  
            defaultBuffer.RemoveRow();  
        }  
    }  
  
    if (defaultBuffer != null)  
        defaultBuffer.SetEndOfRowset();  
  
    if (errorBuffer != null)  
        errorBuffer.SetEndOfRowset();  
}  
```  
  
```vb  
Private columnIndex As Integer()   
Private errorOutputID As Integer = -1   
Private errorOutputIndex As Integer = -1   
  
Public  Overrides Sub PreExecute()   
 Dim defaultOutput As IDTSOutput100 = Nothing   
 Me.GetErrorOutputInfo(errorOutputID, errorOutputIndex)   
 For Each output As IDTSOutput100 In ComponentMetaData.OutputCollection   
   If Not (output.ID = errorOutputID) Then   
     defaultOutput = output   
   End If   
 Next   
 columnIndex = New Integer(defaultOutput.OutputColumnCollection.Count) {}   
 Dim col As Integer = 0   
 While col < defaultOutput.OutputColumnCollection.Count   
   Dim column As IDTSOutputColumn100 = defaultOutput.OutputColumnCollection(col)   
   columnIndex(col) = BufferManager.FindColumnByLineageID(defaultOutput.Buffer, column.LineageID)   
   System.Math.Min(System.Threading.Interlocked.Increment(col),col-1)   
 End While   
End Sub   
  
Public  Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())   
 Dim x As Integer = 0   
 While x < outputs   
   If outputIDs(x) = errorOutputID Then   
     Me.errorBuffer = buffers(x)   
   Else   
     Me.defaultBuffer = buffers(x)   
   End If   
   System.Math.Min(System.Threading.Interlocked.Increment(x),x-1)   
 End While   
 Dim rows As Integer = 100   
 Dim random As Random = New Random(System.DateTime.Now.Millisecond)   
 Dim row As Integer = 0   
 While row < rows   
   Try   
     defaultBuffer.AddRow   
     Dim x As Integer = 0   
     While x < columnIndex.Length   
       defaultBuffer(columnIndex(x)) = random.Next   
       System.Math.Min(System.Threading.Interlocked.Increment(x),x-1)   
     End While   
     ' Simulate an error.  
     If (row Mod 2) = 0 Then   
       Throw New Exception("A simulated error.")   
     End If   
   Catch   
     ' Add a row to the error buffer.  
     errorBuffer.AddRow   
     ' Get the values from the default buffer  
     ' and copy them to the error buffer.  
     Dim x As Integer = 0   
     While x < columnIndex.Length   
       errorBuffer(columnIndex(x)) = defaultBuffer(columnIndex(x))   
       System.Math.Min(System.Threading.Interlocked.Increment(x),x-1)   
     End While   
     ' Set the error information.  
     errorBuffer.SetErrorInfo(errorOutputID, 1, 0)   
     ' Remove the row that was added to the default buffer.  
     defaultBuffer.RemoveRow   
   End Try   
   System.Math.Min(System.Threading.Interlocked.Increment(row),row-1)   
 End While   
 If Not (defaultBuffer Is Nothing) Then   
   defaultBuffer.SetEndOfRowset   
 End If   
 If Not (errorBuffer Is Nothing) Then   
   errorBuffer.SetEndOfRowset   
 End If   
End Sub  
```  
  
<span data-ttu-id="50247-151">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="50247-151">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="50247-152">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="50247-152">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="50247-153">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="50247-153">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="50247-154">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="50247-154">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50247-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50247-155">See Also</span></span>  
 <span data-ttu-id="50247-156">[데이터의 오류 처리](../../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="50247-156">[Error Handling in Data](../../data-flow/error-handling-in-data.md) </span></span>  
 [<span data-ttu-id="50247-157">오류 출력 사용</span><span class="sxs-lookup"><span data-stu-id="50247-157">Using Error Outputs</span></span>](using-error-outputs-in-a-data-flow-component.md)  
  
  
