---
title: 스크립트 구성 요소 개체 모델 이해 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a11556b00efc5749e8ddb895712d6c61f2459d8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650188"
---
# <a name="understanding-the-script-component-object-model"></a><span data-ttu-id="fb944-102">스크립트 구성 요소 개체 모델 이해</span><span class="sxs-lookup"><span data-stu-id="fb944-102">Understanding the Script Component Object Model</span></span>
  <span data-ttu-id="fb944-103">[스크립트 구성 요소 코딩 및 디버깅] (. /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md 스크립트 구성 요소 프로젝트에는 다음 세 개의 프로젝트 항목이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-103">As discussed in [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md, the Script component project contains three project items:</span></span>

1.  <span data-ttu-id="fb944-104">`ScriptMain` 항목: 코드를 작성할 `ScriptMain` 클래스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-104">The `ScriptMain` item, which contains the `ScriptMain` class in which you write your code.</span></span> <span data-ttu-id="fb944-105">`ScriptMain` 클래스는 `UserComponent` 클래스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-105">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

2.  <span data-ttu-id="fb944-106">`ComponentWrapper` 항목: 데이터를 처리하고 패키지와 상호 작용하는 데 사용할 메서드 및 속성이 포함된 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>의 인스턴스인 `UserComponent` 클래스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-106">The `ComponentWrapper` item, which contains the `UserComponent` class, an instance of <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> that contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="fb944-107">`ComponentWrapper` 항목에는 `Connections` 및 `Variables` 컬렉션 클래스도 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-107">The `ComponentWrapper` item also contains `Connections` and `Variables` collection classes.</span></span>

3.  <span data-ttu-id="fb944-108">`BufferWrapper` 항목: 각 입력 및 출력에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>에서 상속되는 클래스와 각 열에 대한 형식화된 속성이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-108">The `BufferWrapper` item, which contains classes that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output, and typed properties for each column.</span></span>

 <span data-ttu-id="fb944-109">`ScriptMain` 항목에서 코드를 작성할 때는 이 항목에 설명된 개체, 메서드 및 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-109">As you write your code in the `ScriptMain` item, you will use the objects, methods, and properties discussed in this topic.</span></span> <span data-ttu-id="fb944-110">각 구성 요소에서 여기에 나열된 메서드를 모두 사용하는 것은 아니지만 사용될 경우에는 여기에 표시된 순서대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-110">Each component will not use all the methods listed here; however, when used, they are used in the sequence shown.</span></span>

 <span data-ttu-id="fb944-111"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 기본 클래스에는 이 항목에 설명된 메서드의 구현 코드가 들어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class does not contain any implementation code for the methods discussed in this topic.</span></span> <span data-ttu-id="fb944-112">따라서 메서드 구현에 기본 클래스 구현에 대한 호출을 추가하는 것은 불필요하지만 해가 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-112">Therefore it is unnecessary, but harmless, to add a call to the base class implementation to your own implementation of the method.</span></span>

 <span data-ttu-id="fb944-113">특정 유형의 스크립트 구성 요소에서 이러한 클래스의 메서드와 속성을 사용하는 방법에 대한 자세한 내용은 [추가 스크립트 구성 요소 예제](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb944-113">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="fb944-114">예 항목에는 전체 코드 예제도 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-114">The example topics also contain complete code samples.</span></span>

## <a name="acquireconnections-method"></a><span data-ttu-id="fb944-115">AcquireConnections 메서드</span><span class="sxs-lookup"><span data-stu-id="fb944-115">AcquireConnections Method</span></span>
 <span data-ttu-id="fb944-116">원본 및 대상은 일반적으로 외부 데이터 원본에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-116">Sources and destinations generally must connect to an external data source.</span></span> <span data-ttu-id="fb944-117"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의하여 적절한 연결 관리자에서 연결 또는 연결 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-117">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to retrieve the connection or the connection information from the appropriate connection manager.</span></span>

 <span data-ttu-id="fb944-118">다음 예에서는 ADO.NET 연결 관리자에서 `System.Data.SqlClient.SqlConnection`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-118">The following example returns a `System.Data.SqlClient.SqlConnection` from an ADO.NET connection manager.</span></span>

```vb
Dim connMgr As IDTSConnectionManager100
Dim sqlConn As SqlConnection

Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    connMgr = Me.Connections.MyADONETConnection
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

End Sub
```

 <span data-ttu-id="fb944-119">다음 예에서는 플랫 파일 연결 관리자에서 전체 경로 및 파일 이름을 반환한 다음 `System.IO.StreamReader`를 사용하여 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-119">The following example returns a complete path and file name from a Flat File Connection Manager, and then opens the file by using a `System.IO.StreamReader`.</span></span>

```vb
Private textReader As StreamReader
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

    Dim connMgr As IDTSConnectionManager100 = _
        Me.Connections.MyFlatFileSrcConnectionManager
    Dim exportedAddressFile As String = _
        CType(connMgr.AcquireConnection(Nothing), String)
    textReader = New StreamReader(exportedAddressFile)

End Sub
```

## <a name="preexecute-method"></a><span data-ttu-id="fb944-120">PreExecute 메서드</span><span class="sxs-lookup"><span data-stu-id="fb944-120">PreExecute Method</span></span>
 <span data-ttu-id="fb944-121">데이터 행의 처리를 시작하기 전에만 한 번 수행해야 하는 처리가 있을 때마다 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-121">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only before you start processing rows of data.</span></span> <span data-ttu-id="fb944-122">예를 들어 대상에서 데이터 원본에 각 데이터 행을 삽입하는 데 사용할 매개 변수가 있는 명령을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-122">For example, in a destination, you may want to configure the parameterized command that the destination will use to insert each row of data into the data source.</span></span>

```vb
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter
...
    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub
```

```csharp
SqlConnection sqlConn; 
SqlCommand sqlCmd; 
SqlParameter sqlParam; 

public override void PreExecute() 
{ 

    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn); 
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int); 
    sqlCmd.Parameters.Add(sqlParam); 
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30); 
    sqlCmd.Parameters.Add(sqlParam); 

}
```

## <a name="processing-inputs-and-outputs"></a><span data-ttu-id="fb944-123">입력 및 출력 처리</span><span class="sxs-lookup"><span data-stu-id="fb944-123">Processing Inputs and Outputs</span></span>

### <a name="processing-inputs"></a><span data-ttu-id="fb944-124">입력 처리</span><span class="sxs-lookup"><span data-stu-id="fb944-124">Processing Inputs</span></span>
 <span data-ttu-id="fb944-125">변환 또는 대상으로 구성된 스크립트 구성 요소에는 하나의 입력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-125">Script components that are configured as transformations or destinations have one input.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="fb944-126">BufferWrapper 프로젝트 항목의 제공 내용</span><span class="sxs-lookup"><span data-stu-id="fb944-126">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="fb944-127">`BufferWrapper` 프로젝트 항목에는 사용자가 구성한 각 입력에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>에서 파생되며 입력과 이름이 동일한 클래스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-127">For each input that you have configured, the `BufferWrapper` project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the input.</span></span> <span data-ttu-id="fb944-128">각 입력 버퍼 클래스에는 다음과 같은 속성, 함수 및 메서드가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-128">Each input buffer class contains the following properties, functions, and methods:</span></span>

-   <span data-ttu-id="fb944-129">선택한 각 입력 열에 대한 명명되고 형식화된 접근자 속성.</span><span class="sxs-lookup"><span data-stu-id="fb944-129">Named, typed accessor properties for each selected input column.</span></span> <span data-ttu-id="fb944-130">이러한 속성은 **스크립트 변환 편집기**의 **입력 열** 페이지에서 열에 대해 지정된 **사용 유형**에 따라 읽기 전용 또는 읽기/쓰기입니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-130">These properties are read-only or read/write depending on the **Usage Type** specified for the column on the **Input Columns** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="fb944-131">선택한 각 입력 열에 대한 **\<column>_IsNull** 속성.</span><span class="sxs-lookup"><span data-stu-id="fb944-131">A **\<column>_IsNull** property for each selected input column.</span></span> <span data-ttu-id="fb944-132">이 속성도 열에 대해 지정된 **사용 유형**에 따라 읽기 전용 또는 읽기/쓰기입니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-132">This property is also read-only or read/write depending on the **Usage Type** specified for the column.</span></span>

-   <span data-ttu-id="fb944-133">구성된 각 출력에 대한 **DirectRowTo\<outputbuffer>** 메서드.</span><span class="sxs-lookup"><span data-stu-id="fb944-133">A **DirectRowTo\<outputbuffer>** method for each configured output.</span></span> <span data-ttu-id="fb944-134">이러한 메서드는 행을 동일한 `ExclusionGroup`의 여러 출력 중 하나로 필터링할 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-134">You will use these methods when filtering rows to one of several outputs in the same `ExclusionGroup`.</span></span>

-   <span data-ttu-id="fb944-135">다음 입력 행을 가져오기 위한 `NextRow` 함수와 데이터의 마지막 버퍼가 처리되었는지 여부를 확인하기 위한 `EndOfRowset` 함수.</span><span class="sxs-lookup"><span data-stu-id="fb944-135">A `NextRow` function to get the next input row, and an `EndOfRowset` function to determine whether the last buffer of data has been processed.</span></span> <span data-ttu-id="fb944-136">일반적으로 `UserComponent` 기본 클래스에 구현된 입력 처리 메서드를 사용할 때는 이러한 함수가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-136">You typically do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span> <span data-ttu-id="fb944-137">다음 섹션에서는 `UserComponent` 기본 클래스에 대한 더 많은 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-137">The next section provides more information about the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="fb944-138">ComponentWrapper 프로젝트 항목의 제공 내용</span><span class="sxs-lookup"><span data-stu-id="fb944-138">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="fb944-139">ComponentWrapper 프로젝트 항목에는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>에서 파생된 `UserComponent`라는 클래스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-139">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="fb944-140">사용자 지정 코드를 작성하는 위치인 `ScriptMain` 클래스는 `UserComponent`에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-140">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="fb944-141">`UserComponent` 클래스에는 다음과 같은 메서드가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-141">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="fb944-142">`ProcessInput` 메서드의 재정의된 구현.</span><span class="sxs-lookup"><span data-stu-id="fb944-142">An overridden implementation of the `ProcessInput` method.</span></span> <span data-ttu-id="fb944-143">이 메서드는 데이터 흐름 엔진에서 런타임에 `PreExecute` 메서드 다음으로 호출하는 메서드이며 여러 번 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-143">This is the method that the data flow engine calls next at run time after the `PreExecute` method, and it may be called multiple times.</span></span> <span data-ttu-id="fb944-144">`ProcessInput`\*\* \<inputbuffer> _ProcessInput\*\* 메서드에 대 한 처리를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-144">`ProcessInput` hands off processing to the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="fb944-145">그런 다음 `ProcessInput` 메서드는 입력 버퍼의 끝을 확인하고 버퍼의 끝에 도달한 경우 재정의 가능한 `FinishOutputs` 메서드와 프라이빗 `MarkOutputsAsFinished` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-145">Then the `ProcessInput` method checks for the end of the input buffer and, if the end of the buffer has been reached, calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="fb944-146">그런 다음 `MarkOutputsAsFinished` 메서드가 마지막 출력 버퍼에서 `SetEndOfRowset`을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-146">The `MarkOutputsAsFinished` method then calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="fb944-147">**\<inputbuffer>_ProcessInput** 메서드의 재정의 가능한 구현.</span><span class="sxs-lookup"><span data-stu-id="fb944-147">An overridable implementation of the **\<inputbuffer>_ProcessInput** method.</span></span> <span data-ttu-id="fb944-148">이 기본 구현은 단순히 각 입력 행을 반복하며 **\<inputbuffer>_ProcessInputRow**를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-148">This default implementation simply loops through each input row and calls **\<inputbuffer>_ProcessInputRow**.</span></span>

-   <span data-ttu-id="fb944-149">**\<inputbuffer>_ProcessInputRow** 메서드의 재정의 가능한 구현.</span><span class="sxs-lookup"><span data-stu-id="fb944-149">An overridable implementation of the **\<inputbuffer>_ProcessInputRow** method.</span></span> <span data-ttu-id="fb944-150">기본 구현은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-150">The default implementation is empty.</span></span> <span data-ttu-id="fb944-151">이 메서드는 일반적으로 사용자 지정 데이터 처리 코드를 작성하기 위해 재정의하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-151">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="fb944-152">사용자 지정 코드로 수행하는 작업</span><span class="sxs-lookup"><span data-stu-id="fb944-152">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="fb944-153">`ScriptMain` 클래스에서 다음 메서드를 사용하여 입력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-153">You can use the following methods to process input in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="fb944-154">**\<inputbuffer>_ProcessInputRow**를 재정의하여 각 입력 행의 데이터를 전달할 때 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-154">Override **\<inputbuffer>_ProcessInputRow** to process the data in each input row as it passes through.</span></span>

-   <span data-ttu-id="fb944-155">입력 행을 반복하면서 추가 작업을 수행해야 하는 경우에만 **\<inputbuffer>_ProcessInput**을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-155">Override **\<inputbuffer>_ProcessInput** only if you have to do something additional while looping through input rows.</span></span> <span data-ttu-id="fb944-156">예를 들어 `EndOfRowset` 모든 행이 처리 된 후 다른 작업을 수행 하기 위해를 테스트 해야 합니다. \*\* \<inputbuffer> _ProcessInputRow\*\* 를 호출 하 여 행 처리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-156">(For example, you have to test for `EndOfRowset` to take some other action after all rows have been processed.) Call **\<inputbuffer>_ProcessInputRow** to perform the row processing.</span></span>

-   <span data-ttu-id="fb944-157">출력을 닫기 전에 출력에 대한 작업을 수행해야 하는 경우 `FinishOutputs`를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-157">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="fb944-158">`ProcessInput` 메서드를 사용하면 이러한 메서드가 적절한 시기에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-158">The `ProcessInput` method ensures that these methods are called at the appropriate times.</span></span>

### <a name="processing-outputs"></a><span data-ttu-id="fb944-159">출력 처리</span><span class="sxs-lookup"><span data-stu-id="fb944-159">Processing Outputs</span></span>
 <span data-ttu-id="fb944-160">원본 또는 변환으로 구성된 스크립트 구성 요소에는 하나 이상의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-160">Script components configured as sources or transformations have one or more outputs.</span></span>

#### <a name="what-the-bufferwrapper-project-item-provides"></a><span data-ttu-id="fb944-161">BufferWrapper 프로젝트 항목의 제공 내용</span><span class="sxs-lookup"><span data-stu-id="fb944-161">What the BufferWrapper Project Item Provides</span></span>
 <span data-ttu-id="fb944-162">BufferWrapper 프로젝트 항목에는 사용자가 구성한 각 출력에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>에서 파생되며 출력과 이름이 동일한 클래스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-162">For each output that you have configured, the BufferWrapper project item contains a class that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> and has the same name as the output.</span></span> <span data-ttu-id="fb944-163">각 입력 버퍼 클래스에는 다음과 같은 속성 및 메서드가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-163">Each input buffer class contains the following properties and methods:</span></span>

-   <span data-ttu-id="fb944-164">각 출력 열에 대한 명명되고 형식화된 쓰기 전용 접근자 속성</span><span class="sxs-lookup"><span data-stu-id="fb944-164">Named, typed, write-only accessor properties for each output column.</span></span>

-   <span data-ttu-id="fb944-165">열 값을로 설정 하는 데 사용할 수 있는 선택 된 각 출력 열에 대 한 쓰기 전용 \*\* \<column> _IsNull\*\* 속성입니다 `null` .</span><span class="sxs-lookup"><span data-stu-id="fb944-165">A write-only **\<column>_IsNull** property for each selected output column that you can use to set the column value to `null`.</span></span>

-   <span data-ttu-id="fb944-166">비어 있는 새 행을 출력 버퍼에 추가하는 데 사용하는 `AddRow` 메서드</span><span class="sxs-lookup"><span data-stu-id="fb944-166">An `AddRow` method to add an empty new row to the output buffer.</span></span>

-   <span data-ttu-id="fb944-167">데이터 흐름 엔진에 데이터 버퍼가 더 이상 없음을 알려 주는 `SetEndOfRowset` 메서드.</span><span class="sxs-lookup"><span data-stu-id="fb944-167">A `SetEndOfRowset` method to let the data flow engine know that no more buffers of data are expected.</span></span> <span data-ttu-id="fb944-168">현재 버퍼가 마지막 데이터 버퍼인지를 확인하기 위한 `EndOfRowset` 함수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-168">There is also an `EndOfRowset` function to determine whether the current buffer is the last buffer of data.</span></span> <span data-ttu-id="fb944-169">일반적으로 `UserComponent` 기본 클래스에 구현된 입력 처리 메서드를 사용할 때는 이러한 함수가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-169">You generally do not need these functions when you use the input processing methods implemented in the `UserComponent` base class.</span></span>

#### <a name="what-the-componentwrapper-project-item-provides"></a><span data-ttu-id="fb944-170">ComponentWrapper 프로젝트 항목의 제공 내용</span><span class="sxs-lookup"><span data-stu-id="fb944-170">What the ComponentWrapper Project Item Provides</span></span>
 <span data-ttu-id="fb944-171">ComponentWrapper 프로젝트 항목에는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>에서 파생된 `UserComponent`라는 클래스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-171">The ComponentWrapper project item contains a class named `UserComponent` that derives from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>.</span></span> <span data-ttu-id="fb944-172">사용자 지정 코드를 작성하는 위치인 `ScriptMain` 클래스는 `UserComponent`에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-172">The `ScriptMain` class in which you write your custom code derives in turn from `UserComponent`.</span></span> <span data-ttu-id="fb944-173">`UserComponent` 클래스에는 다음과 같은 메서드가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-173">The `UserComponent` class contains the following methods:</span></span>

-   <span data-ttu-id="fb944-174">`PrimeOutput` 메서드의 재정의된 구현.</span><span class="sxs-lookup"><span data-stu-id="fb944-174">An overridden implementation of the `PrimeOutput` method.</span></span> <span data-ttu-id="fb944-175">데이터 흐름 엔진에서는 런타임에 이 메서드를 `ProcessInput`보다 먼저 호출하며 이 메서드는 한 번만 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-175">The data flow engine calls this method before `ProcessInput` at run time, and it is only called one time.</span></span> <span data-ttu-id="fb944-176">`PrimeOutput`은 `CreateNewOutputRows` 메서드로 처리를 넘깁니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-176">`PrimeOutput` hands off processing to the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="fb944-177">그런 다음 구성 요소가 원본인 경우, 즉 구성 요소에 입력이 없는 경우 `PrimeOutput`은 재정의 가능한 `FinishOutputs` 메서드와 프라이빗 `MarkOutputsAsFinished` 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-177">Then, if the component is a source (that is, the component has no inputs), `PrimeOutput` calls the overridable `FinishOutputs` method and the private `MarkOutputsAsFinished` method.</span></span> <span data-ttu-id="fb944-178">`MarkOutputsAsFinished` 메서드는 마지막 출력 버퍼에서 `SetEndOfRowset`을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-178">The `MarkOutputsAsFinished` method calls `SetEndOfRowset` on the last output buffer.</span></span>

-   <span data-ttu-id="fb944-179">`CreateNewOutputRows` 메서드의 재정의 가능한 구현.</span><span class="sxs-lookup"><span data-stu-id="fb944-179">An overridable implementation of the `CreateNewOutputRows` method.</span></span> <span data-ttu-id="fb944-180">기본 구현은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-180">The default implementation is empty.</span></span> <span data-ttu-id="fb944-181">이 메서드는 일반적으로 사용자 지정 데이터 처리 코드를 작성하기 위해 재정의하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-181">This is the method that you will normally override to write your custom data processing code.</span></span>

#### <a name="what-your-custom-code-should-do"></a><span data-ttu-id="fb944-182">사용자 지정 코드로 수행하는 작업</span><span class="sxs-lookup"><span data-stu-id="fb944-182">What Your Custom Code Should Do</span></span>
 <span data-ttu-id="fb944-183">`ScriptMain` 클래스에서 다음 메서드를 사용하여 출력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-183">You can use the following methods to process outputs in the `ScriptMain` class:</span></span>

-   <span data-ttu-id="fb944-184">입력 행을 처리하기 전에 출력 행을 추가하고 채울 수 있는 경우에 한해 `CreateNewOutputRows`를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-184">Override `CreateNewOutputRows` only when you can add and populate output rows before processing input rows.</span></span> <span data-ttu-id="fb944-185">예를 들어 원본에서는 `CreateNewOutputRows`를 사용할 수 있지만 비동기 출력을 사용하는 변환에서는 입력 데이터를 처리하는 동안이나 그 이후에 `AddRow`를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-185">For example, you can use `CreateNewOutputRows` in a source, but in a transformation with asynchronous outputs, you should call `AddRow` during or after the processing of input data.</span></span>

-   <span data-ttu-id="fb944-186">출력을 닫기 전에 출력에 대한 작업을 수행해야 하는 경우 `FinishOutputs`를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-186">Override `FinishOutputs` if you have to do something to the outputs before they are closed.</span></span>

 <span data-ttu-id="fb944-187">`PrimeOutput` 메서드를 사용하면 이러한 메서드가 적절한 시기에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-187">The `PrimeOutput` method ensures that these methods are called at the appropriate times.</span></span>

## <a name="postexecute-method"></a><span data-ttu-id="fb944-188">PostExecute 메서드</span><span class="sxs-lookup"><span data-stu-id="fb944-188">PostExecute Method</span></span>
 <span data-ttu-id="fb944-189">데이터 행의 처리를 시작한 후에만 한 번 수행해야 하는 처리가 있을 때마다 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-189">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class whenever you have processing that you must perform one time only after you have processed the rows of data.</span></span> <span data-ttu-id="fb944-190">예를 들어 원본에서는 데이터 흐름으로 데이터를 로드하는 데 사용한 `System.Data.SqlClient.SqlDataReader`를 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-190">For example, in a source, you may want to close the `System.Data.SqlClient.SqlDataReader` that you have used to load data into the data flow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="fb944-191">`ReadWriteVariables`의 컬렉션은 `PostExecute` 메서드에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-191">The collection of `ReadWriteVariables` is available only in the `PostExecute` method.</span></span> <span data-ttu-id="fb944-192">따라서 각 데이터 행을 처리할 때 패키지 변수의 값을 직접 증분시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-192">Therefore you cannot directly increment the value of a package variable as you process each row of data.</span></span> <span data-ttu-id="fb944-193">대신 지역 변수의 값을 증분시키고 모든 데이터가 처리된 후에 `PostExecute` 메서드에서 패키지 변수의 값을 지역 변수 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-193">Instead, increment the value of a local variable, and set the value of the package variable to the value of the local variable in the `PostExecute` method after all data has been processed.</span></span>

## <a name="releaseconnections-method"></a><span data-ttu-id="fb944-194">ReleaseConnections 메서드</span><span class="sxs-lookup"><span data-stu-id="fb944-194">ReleaseConnections Method</span></span>
 <span data-ttu-id="fb944-195">원본과 대상은 일반적으로 외부 데이터 원본에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-195">Sources and destinations typically must connect to an external data source.</span></span> <span data-ttu-id="fb944-196"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 메서드를 재정의하여 이전에 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> 메서드에서 연 연결을 닫고 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="fb944-196">Override the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> base class to close and release the connection that you have opened previously in the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> method.</span></span>

```vb
    Dim connMgr As IDTSConnectionManager100
...
    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub
```

```csharp
IDTSConnectionManager100 connMgr;

public override void ReleaseConnections()
{

    connMgr.ReleaseConnection(sqlConn);

}
```

<span data-ttu-id="fb944-197">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="fb944-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="fb944-198">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="fb944-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="fb944-199">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="fb944-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="fb944-200">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="fb944-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb944-201">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb944-201">See Also</span></span>
 <span data-ttu-id="fb944-202">스크립트 구성 요소 [편집기에서 스크립트](configuring-the-script-component-in-the-script-component-editor.md) 구성 요소 구성 [스크립트 구성 요소 코딩 및 디버깅] (... /extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span><span class="sxs-lookup"><span data-stu-id="fb944-202">[Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md) [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md</span></span>


