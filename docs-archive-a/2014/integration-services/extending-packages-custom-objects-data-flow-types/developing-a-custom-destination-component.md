---
title: 사용자 지정 대상 구성 요소 개발 | Microsoft Docs
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
- validation [Integration Services], components
- destinations [Integration Services], components
- ProcessInput method
- external data sources [Integration Services]
- custom data flow components [Integration Services], destination components
- data flow components [Integration Services], destination components
ms.assetid: 24619363-9535-4c0e-8b62-1d22c6630e40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6979d14afa0490638162c35bb660f15506803484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727296"
---
# <a name="developing-a-custom-destination-component"></a><span data-ttu-id="a02cf-102">사용자 지정 대상 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="a02cf-102">Developing a Custom Destination Component</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a02cf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 개발자가 사용자 지정 데이터 원본에 연결하여 데이터를 저장할 수 있는 사용자 지정 대상 구성 요소를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] gives developers the ability to write custom destination components that can connect to and store data in any custom data source.</span></span> <span data-ttu-id="a02cf-104">사용자 지정 대상 구성 요소는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 기존 원본 구성 요소 중 하나를 사용하여 액세스할 수 없는 데이터 원본에 연결해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-104">Custom destination components are useful when you need to connect to data sources that cannot be accessed by using one of the existing source components included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="a02cf-105">대상 구성 요소에는 하나 이상의 입력이 있으며 출력은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-105">Destination components have one or more inputs and zero outputs.</span></span> <span data-ttu-id="a02cf-106">대상 구성 요소에서는 디자인 타임에 연결을 만들고 구성하며 외부 데이터 원본에서 열 메타데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-106">At design time, they create and configure connections and read column metadata from the external data source.</span></span> <span data-ttu-id="a02cf-107">또한 실행 중에는 외부 데이터 원본에 연결하고 데이터 흐름의 업스트림 구성 요소에서 받은 행을 외부 데이터 원본에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-107">During execution, they connect to their external data source and add rows that are received from the components upstream in the data flow to the external data source.</span></span> <span data-ttu-id="a02cf-108">구성 요소를 실행하기 전에 이미 외부 데이터 원본이 있는 경우 대상 구성 요소에서는 받은 열의 데이터 형식과 외부 데이터 원본에 있는 열의 데이터 형식이 일치하는지도 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-108">If the external data source exists prior to execution of the component, the destination component must also ensure that the data types of the columns that the component receives match the data types of the columns at the external data source.</span></span>

 <span data-ttu-id="a02cf-109">이 섹션에서는 대상 구성 요소의 개발 방법을 자세히 설명하고 중요한 개념을 명확하게 보여 주는 코드 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-109">This section discusses the details of how to develop destination components, and provides code examples to clarify important concepts.</span></span> <span data-ttu-id="a02cf-110">데이터 흐름 구성 요소 개발에 대한 일반적인 개요는 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a02cf-110">For a general overview of data flow component development, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="a02cf-111">디자인 타임</span><span class="sxs-lookup"><span data-stu-id="a02cf-111">Design Time</span></span>
 <span data-ttu-id="a02cf-112">대상 구성 요소의 디자인 타임 기능을 구현하려면 외부 데이터 원본에 대한 연결을 지정하고 구성 요소가 올바르게 구성되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-112">Implementing the design-time functionality of a destination component involves specifying a connection to an external data source and validating that the component has been correctly configured.</span></span> <span data-ttu-id="a02cf-113">정의에 따라 대상 구성 요소에는 하나의 입력이 있으며 하나의 오류 출력이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-113">By definition, a destination component has one input and possibly one error output.</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="a02cf-114">구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="a02cf-114">Creating the Component</span></span>
 <span data-ttu-id="a02cf-115">대상 구성 요소는 패키지에 정의된 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체를 사용하여 외부 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-115">Destination components connect to external data sources by using <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects defined in a package.</span></span> <span data-ttu-id="a02cf-116">대상 구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 컬렉션에 요소를 추가하여 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너와 구성 요소 사용자에게 연결 관리자가 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-116">The destination component indicates its requirement for a connection manager to the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, and to users of the component, by adding an element to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>.</span></span> <span data-ttu-id="a02cf-117">이 컬렉션은 두 가지 용도로 사용됩니다. 첫 번째는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에 연결 관리자가 필요함을 알리는 것이고, 다른 하나는 사용자가 연결 관리자를 선택하거나 만든 후 구성 요소에서 사용하는 패키지에 해당 연결 관리자에 대한 참조를 저장하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-117">This collection serves two purposes: first, it advertises the need for a connection manager to [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer; then, after the user has selected or created a connection manager, it holds a reference to the connection manager in the package that is being used by the component.</span></span> <span data-ttu-id="a02cf-118">컬렉션에 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100>을 추가하면 **고급 편집기**에 **연결 속성** 탭이 표시되어 사용자가 구성 요소에서 사용할 패키지에서 연결을 선택하거나 만들도록 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-118">When an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> is added to the collection, the **Advanced Editor** displays the **Connection Properties** tab, to prompt the user to select or create a connection in the package for use by the component.</span></span>

 <span data-ttu-id="a02cf-119">다음 코드 예제에서는 입력을 추가한 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>에 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> 개체를 추가하는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-119">The following code sample shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that adds an input, and then adds a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> object to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "Destination Component",ComponentType =ComponentType.DestinationAdapter)]
    public class DestinationComponent : PipelineComponent 
    {
        public override void ProvideComponentProperties()
        {
            // Reset the component.
            base.RemoveAllInputsOutputsAndCustomProperties();
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();

            IDTSInput100 input = ComponentMetaData.InputCollection.New();
            input.Name = "Input";

            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();
            connection.Name = "ADO.net";
        }
    }
}
```

```vb
Imports System
Imports System.Data
Imports System.Data.SqlClient
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime

Namespace Microsoft.Samples.SqlServer.Dts

    <DtsPipelineComponent(DisplayName:="Destination Component", ComponentType:=ComponentType.DestinationAdapter)> _
    Public Class DestinationComponent
        Inherits PipelineComponent

        Public Overrides Sub ProvideComponentProperties()

            ' Reset the component.
            Me.RemoveAllInputsOutputsAndCustomProperties()
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll()

            Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()
            input.Name = "Input"

            Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()
            connection.Name = "ADO.net"

        End Sub
    End Class
End Namespace
```

### <a name="connecting-to-an-external-data-source"></a><span data-ttu-id="a02cf-120">외부 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="a02cf-120">Connecting to an External Data Source</span></span>
 <span data-ttu-id="a02cf-121"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>에 연결을 추가한 후에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 메서드를 재정의하여 외부 데이터 원본에 대한 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-121">After a connection is added to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>, you override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method to establish a connection to the external data source.</span></span> <span data-ttu-id="a02cf-122">이 메서드는 디자인 타임과 런타임에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-122">This method is called at design time and at run time.</span></span> <span data-ttu-id="a02cf-123">구성 요소에서는 런타임 연결에 지정된 연결 관리자에 대한 연결을 설정한 후 외부 데이터 원본에 대한 연결을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-123">The component must establish a connection to the connection manager specified by the run-time connection, and subsequently, to the external data source.</span></span> <span data-ttu-id="a02cf-124">연결이 설정되면 구성 요소에서는 연결을 내부에 캐시했다가 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>가 호출되면 이를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-124">Once established, the component should cache the connection internally and release it when <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> is called.</span></span> <span data-ttu-id="a02cf-125">개발자는 이 메서드를 재정의하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 실행 중에 구성 요소에서 설정한 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-125">Developers override this method, and release the connection established by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span> <span data-ttu-id="a02cf-126"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 메서드는 모두 디자인 타임과 런타임에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-126">Both of these methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>, are called at design time and at run time.</span></span>

 <span data-ttu-id="a02cf-127">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 메서드에서 ADO.NET 연결에 연결한 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>에서 연결을 닫는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-127">The following code example shows a component that connects to an ADO.NET connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method, and then closes the connection in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>.</span></span>

```csharp
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

private SqlConnection sqlConnection;

public override void AcquireConnections(object transaction)
{
    if (ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager != null)
    {
        ConnectionManager cm = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager);
        ConnectionManagerAdoNet cmado = cm.InnerObject as ConnectionManagerAdoNet;

        if (cmado == null)
            throw new Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.");

        sqlConnection = cmado.AcquireConnection(transaction) as SqlConnection;
        sqlConnection.Open();
    }
}

public override void ReleaseConnections()
{
    if (sqlConnection != null && sqlConnection.State != ConnectionState.Closed)
        sqlConnection.Close();
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

Private sqlConnection As SqlConnection

Public Overrides Sub AcquireConnections(ByVal transaction As Object)

    If IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) = False Then

        Dim cm As ConnectionManager = DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject,ConnectionManagerAdoNet)

        If IsNothing(cmado) Then
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")
        End If

        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)
        sqlConnection.Open()

    End If
End Sub

Public Overrides Sub ReleaseConnections()

    If IsNothing(sqlConnection) = False And sqlConnection.State <> ConnectionState.Closed Then
        sqlConnection.Close()
    End If

End Sub
```

### <a name="validating-the-component"></a><span data-ttu-id="a02cf-128">구성 요소 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="a02cf-128">Validating the Component</span></span>
 <span data-ttu-id="a02cf-129">대상 구성 요소 개발자는 [구성 요소 유효성 검사](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)에서 설명한 대로 유효성 검사를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-129">Destination component developers should perform validation as described in [Component Validation](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md).</span></span> <span data-ttu-id="a02cf-130">또한 구성 요소의 입력 열 컬렉션에 정의된 열과 외부 데이터 원본에 있는 열의 데이터 형식 속성이 일치하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-130">In addition, they should verify that the data type properties of the columns defined in the component's input column collection match the columns at the external data source.</span></span> <span data-ttu-id="a02cf-131">때로는 구성 요소 또는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 연결이 끊어진 상태이거나 서버 왕복이 허용되지 않을 때와 같이 외부 데이터 원본을 기준으로 입력 열의 유효성을 검사하는 것이 불가능하거나 바람직하지 않은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-131">At times, verifying the input columns against the external data source can be impossible or undesirable, such as when the component or the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is in a disconnected state, or when round trips to the server are not acceptable.</span></span> <span data-ttu-id="a02cf-132">이러한 경우에도 입력 개체의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ExternalMetadataColumnCollection%2A>을 사용하여 입력 열 컬렉션의 열에 대한 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-132">In these situations, the columns in the input column collection can still be validated by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100.ExternalMetadataColumnCollection%2A> of the input object.</span></span>

 <span data-ttu-id="a02cf-133">이 컬렉션은 입력 개체와 출력 개체 모두에 있으며 구성 요소 개발자는 외부 데이터 원본의 열로 이 컬렉션을 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-133">This collection exists on both input and output objects and must be populated by the component developer from the columns at the external data source.</span></span> <span data-ttu-id="a02cf-134">이 컬렉션은 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너가 오프라인 상태이거나 구성 요소의 연결이 끊어져 있거나 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 속성이 `false`인 경우 입력 열의 유효성을 검사하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-134">This collection can be used to validate the input columns when the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is offline, when the component is disconnected, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span>

 <span data-ttu-id="a02cf-135">다음 예제 코드에서는 기존 입력 열을 기반으로 외부 메타데이터 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-135">The following sample code adds an external metadata column based on an existing input column.</span></span>

```csharp
private void AddExternalMetaDataColumn(IDTSInput100 input,IDTSInputColumn100 inputColumn)
{
    // Set the properties of the external metadata column.
    IDTSExternalMetadataColumn100 externalColumn = input.ExternalMetadataColumnCollection.New();
    externalColumn.Name = inputColumn.Name;
    externalColumn.Precision = inputColumn.Precision;
    externalColumn.Length = inputColumn.Length;
    externalColumn.DataType = inputColumn.DataType;
    externalColumn.Scale = inputColumn.Scale;

    // Map the external column to the input column.
    inputColumn.ExternalMetadataColumnID = externalColumn.ID;
}
```

```vb
Private Sub AddExternalMetaDataColumn(ByVal input As IDTSInput100, ByVal inputColumn As IDTSInputColumn100)

    ' Set the properties of the external metadata column.
    Dim externalColumn As IDTSExternalMetadataColumn100 = input.ExternalMetadataColumnCollection.New()
    externalColumn.Name = inputColumn.Name
    externalColumn.Precision = inputColumn.Precision
    externalColumn.Length = inputColumn.Length
    externalColumn.DataType = inputColumn.DataType
    externalColumn.Scale = inputColumn.Scale

    ' Map the external column to the input column.
    inputColumn.ExternalMetadataColumnID = externalColumn.ID

End Sub
```

## <a name="run-time"></a><span data-ttu-id="a02cf-136">런타임</span><span class="sxs-lookup"><span data-stu-id="a02cf-136">Run Time</span></span>
 <span data-ttu-id="a02cf-137">실행 중 대상 구성 요소는 업스트림 구성 요소에서 전체 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>를 사용할 수 있을 때마다 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 메서드에 대한 호출을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-137">During execution, the destination component receives a call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method each time a full <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> is available from the upstream component.</span></span> <span data-ttu-id="a02cf-138">이 메서드는 사용할 수 있는 버퍼가 더 이상 없고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 속성이 `true`일 때까지 반복적으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-138">This method is called repeatedly until there are no more buffers available and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property is `true`.</span></span> <span data-ttu-id="a02cf-139">이 메서드가 실행되는 동안 대상 구성 요소에서는 버퍼의 열과 행을 읽고 이를 외부 데이터 원본에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-139">During this method, destination components read columns and rows in the buffer, and add them to the external data source.</span></span>

### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="a02cf-140">버퍼에서 열 찾기</span><span class="sxs-lookup"><span data-stu-id="a02cf-140">Locating Columns in the Buffer</span></span>
 <span data-ttu-id="a02cf-141">구성 요소의 입력 버퍼에는 데이터 흐름에서 해당 구성 요소에 대한 업스트림 구성 요소의 출력 열 컬렉션에 정의된 모든 열이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-141">The input buffer for a component contains all the columns defined in the output column collections of the components upstream from the component in the data flow.</span></span> <span data-ttu-id="a02cf-142">예를 들어 원본 구성 요소에서 출력에 세 개의 열을 제공하고 다음 구성 요소에서 추가 출력 열을 하나 추가할 경우, 대상 구성 요소에서 두 개의 열만 작성하더라도 대상 구성 요소에 제공된 버퍼에는 네 개의 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-142">For example, if a source component provides three columns in its output, and the next component adds an additional output column, the buffer provided to the destination component contains four columns, even if the destination component will write only two columns.</span></span>

 <span data-ttu-id="a02cf-143">입력 버퍼의 열 순서는 대상 구성 요소의 입력 열 컬렉션에 있는 열의 인덱스로 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-143">The order of the columns in the input buffer is not defined by the index of the column in the input column collection of the destination component.</span></span> <span data-ttu-id="a02cf-144">따라서 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 메서드를 사용해야 버퍼 행에서 열을 안정적으로 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-144">Columns can be reliably located in a buffer row only by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="a02cf-145">이 메서드는 지정된 버퍼에서 지정된 계보 ID가 있는 열을 찾고 해당 위치를 행에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-145">This method locates the column that has the specified lineage ID in the specified buffer, and returns its location in the row.</span></span> <span data-ttu-id="a02cf-146">입력 열의 인덱스는 일반적으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 메서드 실행 중에 검색되며 나중에 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 실행 중에 사용할 수 있도록 개발자에 의해 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-146">The indexes of the input columns are typically located during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, and cached by the developer for use later during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>

 <span data-ttu-id="a02cf-147">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 실행 중 버퍼에서 입력 열의 위치를 찾고 이를 배열에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-147">The following code example finds the location of the input columns in the buffer during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> and stores them in an array.</span></span> <span data-ttu-id="a02cf-148">이 배열은 이후 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 실행 중에 버퍼의 열 값을 읽는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-148">The array is subsequently used during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> to read the values of the columns in the buffer.</span></span>

```csharp
int[] cols;

public override void PreExecute()
{
    IDTSInput100 input = ComponentMetaData.InputCollection[0];

    cols = new int[input.InputColumnCollection.Count];

    for (int x = 0; x < input.InputColumnCollection.Count; x++)
    {
        cols[x] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[x].LineageID);
    }
}
```

```vb
Private cols As Integer()

Public Overrides Sub PreExecute()

    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)

    ReDim cols(input.InputColumnCollection.Count)

    For x As Integer = 0 To input.InputColumnCollection.Count

        cols(x) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(x).LineageID)
    Next x

End Sub
```

### <a name="processing-rows"></a><span data-ttu-id="a02cf-149">행 처리</span><span class="sxs-lookup"><span data-stu-id="a02cf-149">Processing Rows</span></span>
 <span data-ttu-id="a02cf-150">버퍼에서 입력 열을 찾은 후에는 해당 입력 열을 읽고 외부 데이터 원본에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-150">Once the input columns have been located in the buffer, they can be read and written to the external data source.</span></span>

 <span data-ttu-id="a02cf-151">대상 구성 요소에서 외부 데이터 원본에 행을 쓰는 동안 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> 메서드를 호출하여 "Rows read" 또는 "BLOB bytes read" 성능 카운터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-151">While the destination component writes rows to the external data source, you may want to update the "Rows read" or "BLOB bytes read" performance counters by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> method.</span></span> <span data-ttu-id="a02cf-152">자세한 내용은 [성능 카운터](../performance/performance-counters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a02cf-152">For more information, see [Performance Counters](../performance/performance-counters.md).</span></span>

 <span data-ttu-id="a02cf-153">다음 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>에 제공된 버퍼에서 행을 읽는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-153">The following example shows a component that reads rows from the buffer provided in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span> <span data-ttu-id="a02cf-154">버퍼에 있는 열의 인덱스는 위의 코드 예에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 실행 중 찾은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-154">The indexes of the columns in the buffer were located during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> in the preceding code example.</span></span>

```csharp
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
        while (buffer.NextRow())
        {
            foreach (int col in cols)
            {
                if (!buffer.IsNull(col))
                {
                    //  TODO: Read the column data.
                }
            }
        }
}
```

```vb
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)

        While (buffer.NextRow())

            For Each col As Integer In cols

                If buffer.IsNull(col) = False Then

                    '  TODO: Read the column data.
                End If

            Next col
        End While
End Sub
```

## <a name="sample"></a><span data-ttu-id="a02cf-155">샘플</span><span class="sxs-lookup"><span data-stu-id="a02cf-155">Sample</span></span>
 <span data-ttu-id="a02cf-156">다음 예제에서는 파일 연결 관리자를 사용하여 데이터 흐름의 이진 데이터를 파일에 저장하는 간단한 대상 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-156">The following sample shows a simple destination component that uses a File connection manager to save binary data from the data flow into files.</span></span> <span data-ttu-id="a02cf-157">이 예제는 이 항목에 설명된 메서드 및 기능의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-157">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="a02cf-158">또한 모든 사용자 지정 대상 구성 요소에서 재정의해야 하는 중요한 메서드를 보여 주지만 디자인 타임 유효성 검사를 위한 코드는 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a02cf-158">It demonstrates the important methods that every custom destination component must override, but does not contain code for design-time validation.</span></span>

```csharp
using System;
using System.IO;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace BlobDst
{
  [DtsPipelineComponent(DisplayName = "BLOB Extractor Destination", Description = "Writes values of BLOB columns to files")]
  public class BlobDst : PipelineComponent
  {
    string m_DestDir;
    int m_FileNameColumnIndex = -1;
    int m_BlobColumnIndex = -1;

    public override void ProvideComponentProperties()
    {
      IDTSInput100 input = ComponentMetaData.InputCollection.New();
      input.Name = "BLOB Extractor Destination Input";
      input.HasSideEffects = true;

      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();
      conn.Name = "FileConnection";
    }

    public override void AcquireConnections(object transaction)
    {
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];
      m_DestDir = (string)conn.ConnectionManager.AcquireConnection(null);

      if (m_DestDir.Length > 0 && m_DestDir[m_DestDir.Length - 1] != '\\')
        m_DestDir += "\\";
    }

    public override IDTSInputColumn100 SetUsageType(int inputID, IDTSVirtualInput100 virtualInput, int lineageID, DTSUsageType usageType)
    {
      IDTSInputColumn100 inputColumn = base.SetUsageType(inputID, virtualInput, lineageID, usageType);
      IDTSCustomProperty100 custProp;

      custProp = inputColumn.CustomPropertyCollection.New();
      custProp.Name = "IsFileName";
      custProp.Value = (object)false;

      custProp = inputColumn.CustomPropertyCollection.New();
      custProp.Name = "IsBLOB";
      custProp.Value = (object)false;

      return inputColumn;
    }

    public override void PreExecute()
    {
      IDTSInput100 input = ComponentMetaData.InputCollection[0];
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;
      IDTSCustomProperty100 custProp;

      foreach (IDTSInputColumn100 column in inputColumns)
      {
        custProp = column.CustomPropertyCollection["IsFileName"];
        if ((bool)custProp.Value == true)
        {
          m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID);
        }

        custProp = column.CustomPropertyCollection["IsBLOB"];
        if ((bool)custProp.Value == true)
        {
          m_BlobColumnIndex = (int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID);
        }
      }
    }

    public override void ProcessInput(int inputID, PipelineBuffer buffer)
    {
      while (buffer.NextRow())
      {
        string strFileName = buffer.GetString(m_FileNameColumnIndex);
        int blobLength = (int)buffer.GetBlobLength(m_BlobColumnIndex);
        byte[] blobData = buffer.GetBlobData(m_BlobColumnIndex, 0, blobLength);

        strFileName = TranslateFileName(strFileName);

        // Make sure directory exists before creating file.
        FileInfo fi = new FileInfo(strFileName);
        if (!fi.Directory.Exists)
          fi.Directory.Create();

        // Write the data to the file.
        FileStream fs = new FileStream(strFileName, FileMode.Create, FileAccess.Write, FileShare.None);
        fs.Write(blobData, 0, blobLength);
        fs.Close();
      }
    }

    private string TranslateFileName(string fileName)
    {
      if (fileName.Length > 2 && fileName[1] == ':')
        return m_DestDir + fileName.Substring(3, fileName.Length - 3);
      else
        return m_DestDir + fileName;
    }
  }
}
```

```vb
Imports System 
Imports System.IO 
Imports Microsoft.SqlServer.Dts.Pipeline 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Namespace BlobDst 

 <DtsPipelineComponent(DisplayName="BLOB Extractor Destination", Description="Writes values of BLOB columns to files")> _ 
 Public Class BlobDst 
 Inherits PipelineComponent 
   Private m_DestDir As String 
   Private m_FileNameColumnIndex As Integer = -1 
   Private m_BlobColumnIndex As Integer = -1 

   Public  Overrides Sub ProvideComponentProperties() 
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New 
     input.Name = "BLOB Extractor Destination Input" 
     input.HasSideEffects = True 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New 
     conn.Name = "FileConnection" 
   End Sub 

   Public  Overrides Sub AcquireConnections(ByVal transaction As Object) 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0) 
     m_DestDir = CType(conn.ConnectionManager.AcquireConnection(Nothing), String) 
     If m_DestDir.Length > 0 AndAlso Not (m_DestDir(m_DestDir.Length - 1) = "\"C) Then 
       m_DestDir += "\" 
     End If 
   End Sub 

   Public  Overrides Function SetUsageType(ByVal inputID As Integer, ByVal virtualInput As IDTSVirtualInput100, ByVal lineageID As Integer, ByVal usageType As DTSUsageType) As IDTSInputColumn100 
     Dim inputColumn As IDTSInputColumn100 = MyBase.SetUsageType(inputID, virtualInput, lineageID, usageType) 
     Dim custProp As IDTSCustomProperty100 
     custProp = inputColumn.CustomPropertyCollection.New 
     custProp.Name = "IsFileName" 
     custProp.Value = CType(False, Object) 
     custProp = inputColumn.CustomPropertyCollection.New 
     custProp.Name = "IsBLOB" 
     custProp.Value = CType(False, Object) 
     Return inputColumn 
   End Function 

   Public  Overrides Sub PreExecute() 
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0) 
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection 
     Dim custProp As IDTSCustomProperty100 
     For Each column As IDTSInputColumn100 In inputColumns 
       custProp = column.CustomPropertyCollection("IsFileName") 
       If CType(custProp.Value, Boolean) = True Then 
         m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer) 
       End If 
       custProp = column.CustomPropertyCollection("IsBLOB") 
       If CType(custProp.Value, Boolean) = True Then 
         m_BlobColumnIndex = CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer) 
       End If 
     Next 
   End Sub 

   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
     While buffer.NextRow 
       Dim strFileName As String = buffer.GetString(m_FileNameColumnIndex) 
       Dim blobLength As Integer = CType(buffer.GetBlobLength(m_BlobColumnIndex), Integer) 
       Dim blobData As Byte() = buffer.GetBlobData(m_BlobColumnIndex, 0, blobLength) 
       strFileName = TranslateFileName(strFileName) 
       Dim fi As FileInfo = New FileInfo(strFileName) 
       ' Make sure directory exists before creating file.
       If Not fi.Directory.Exists Then 
         fi.Directory.Create 
       End If 
       ' Write the data to the file.
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Create, FileAccess.Write, FileShare.None) 
       fs.Write(blobData, 0, blobLength) 
       fs.Close 
     End While 
   End Sub 

   Private Function TranslateFileName(ByVal fileName As String) As String 
     If fileName.Length > 2 AndAlso fileName(1) = ":"C Then 
       Return m_DestDir + fileName.Substring(3, fileName.Length - 3) 
     Else 
       Return m_DestDir + fileName 
     End If 
   End Function 
 End Class 
End Namespace
```

<span data-ttu-id="a02cf-159">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="a02cf-159">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a02cf-160">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a02cf-160">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a02cf-161">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="a02cf-161">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a02cf-162">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="a02cf-162">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="a02cf-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a02cf-163">See Also</span></span>
 <span data-ttu-id="a02cf-164">[사용자 지정 원본 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) [스크립트 구성 요소를 사용 하 여 대상 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="a02cf-164">[Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)</span></span>


