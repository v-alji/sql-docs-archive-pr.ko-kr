---
title: 사용자 지정 원본 구성 요소 개발 | Microsoft Docs
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
- validation [Integration Services], components
- external data sources [Integration Services]
- data flow components [Integration Services], source components
- output columns [Integration Services]
- custom data flow components [Integration Services], source components
- custom sources [Integration Services]
- source components [Integration Services]
ms.assetid: 4dc0f631-8fd6-4007-b573-ca67f58ca068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6679b28463a09efe069235a5aef9dca54a381d62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736621"
---
# <a name="developing-a-custom-source-component"></a><span data-ttu-id="aa1d1-102">사용자 지정 원본 구성 요소 개발</span><span class="sxs-lookup"><span data-stu-id="aa1d1-102">Developing a Custom Source Component</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aa1d1-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 개발자가 사용자 지정 데이터 원본에 연결하고 해당 원본의 데이터를 데이터 흐름 태스크의 다른 구성 요소에 제공할 수 있는 원본 구성 요소를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] gives developers the ability to write source components that can connect to custom data sources and supply data from those sources to other components in a data flow task.</span></span> <span data-ttu-id="aa1d1-104">사용자 지정 원본을 만드는 기능은 기존 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 중 하나를 사용하여 액세스할 수 없는 데이터 원본에 연결해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-104">The ability to create custom sources is valuable when you must connect to data sources that cannot be accessed by using one of the existing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources.</span></span>

 <span data-ttu-id="aa1d1-105">원본 구성 요소에는 하나 이상의 출력이 있으며 입력은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-105">Source components have one or more outputs and zero inputs.</span></span> <span data-ttu-id="aa1d1-106">디자인 타임에 원본 구성 요소는 연결을 만들어 구성하고, 외부 데이터 원본에서 열 메타데이터를 읽고, 외부 데이터 원본을 기반으로 원본의 출력 열을 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-106">At design time, source components are used to create and configure connections, read column metadata from the external data source, and configure the source's output columns based on the external data source.</span></span> <span data-ttu-id="aa1d1-107">실행 중 원본 구성 요소는 외부 데이터 원본에 연결하고 출력 버퍼에 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-107">During execution they connect to the external data source and add rows to an output buffer.</span></span> <span data-ttu-id="aa1d1-108">그런 다음 데이터 흐름 태스크에서는 다운스트림 구성 요소에 이 데이터 행 버퍼를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-108">The data flow task then provides this buffer of data rows to downstream components.</span></span>

 <span data-ttu-id="aa1d1-109">데이터 흐름 구성 요소 개발에 대한 일반적인 개요는 [사용자 지정 데이터 흐름 구성 요소 개발](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-109">For a general overview of data flow component development, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="aa1d1-110">디자인 타임</span><span class="sxs-lookup"><span data-stu-id="aa1d1-110">Design Time</span></span>
 <span data-ttu-id="aa1d1-111">원본 구성 요소의 디자인 타임 기능을 구현하려면 외부 데이터 원본에 대한 연결을 지정하고, 데이터 원본을 반영하는 출력 열을 추가 및 구성하고, 구성 요소를 실행할 준비가 되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-111">Implementing the design-time functionality of a source component involves specifying a connection to an external data source, adding and configuring output columns that reflect the data source, and validating that the component is ready to execute.</span></span> <span data-ttu-id="aa1d1-112">정의에 따라 원본 구성 요소에는 입력이 없으며 하나 이상의 비동기 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-112">By definition, a source component has zero inputs and one or more asynchronous outputs.</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="aa1d1-113">구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="aa1d1-113">Creating the Component</span></span>
 <span data-ttu-id="aa1d1-114">원본 구성 요소는 패키지에 정의된 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체를 사용하여 외부 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-114">Source components connect to external data sources by using <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects defined in a package.</span></span> <span data-ttu-id="aa1d1-115">원본 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 속성의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 컬렉션에 요소를 추가하여 연결 관리자가 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-115">They indicate their requirement for a connection manager by adding an element to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="aa1d1-116">이 컬렉션은 두 가지 용도로 사용됩니다. 첫 번째는 구성 요소에서 사용하는 패키지에 연결 관리자에 대한 참조를 저장하는 것이고 다른 하나는 디자이너에 연결 관리자가 필요함을 알리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-116">This collection serves two purposes-to hold references to connection managers in the package used by the component, and to advertise the need for a connection manager to the designer.</span></span> <span data-ttu-id="aa1d1-117"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100>을 컬렉션에 추가하면 **고급 편집기**에 **연결 속성** 탭이 표시되어 사용자가 패키지에서 연결을 선택하거나 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-117">When an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> has been added to the collection, the **Advanced Editor** displays the **Connection Properties** tab, which lets users select or create a connection in the package.</span></span>

 <span data-ttu-id="aa1d1-118">다음 코드 예에서는 출력을 추가하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>에 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> 개체를 추가하는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that adds an output, and adds a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> object to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span>

```csharp
using System;
using System.Collections;
using System.Data;
using System.Data.SqlClient;
using System.Data.OleDb;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "MySourceComponent",ComponentType = ComponentType.SourceAdapter)]
    public class MyComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Reset the component.
            base.RemoveAllInputsOutputsAndCustomProperties();
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();

            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();
            output.Name = "Output";

            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();
            connection.Name = "ADO.NET";
        }
```

```vb
Imports System.Data
Imports System.Data.SqlClient
Imports Microsoft.SqlServer.Dts.Runtime
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper

<DtsPipelineComponent(DisplayName:="MySourceComponent", ComponentType:=ComponentType.SourceAdapter)> _
Public Class MySourceComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Allow for resetting the component.
        RemoveAllInputsOutputsAndCustomProperties()
        ComponentMetaData.RuntimeConnectionCollection.RemoveAll()

        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()
        output.Name = "Output"

        Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()
        connection.Name = "ADO.NET"

    End Sub
End Class
```

### <a name="connecting-to-an-external-data-source"></a><span data-ttu-id="aa1d1-119">외부 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="aa1d1-119">Connecting to an External Data Source</span></span>
 <span data-ttu-id="aa1d1-120"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>에 연결을 추가한 후에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 메서드를 재정의하여 외부 데이터 원본에 대한 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-120">After a connection has been added to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>, you override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method to establish a connection to the external data source.</span></span> <span data-ttu-id="aa1d1-121">이 메서드는 디자인 및 실행 중에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-121">This method is called during both design and execution time.</span></span> <span data-ttu-id="aa1d1-122">구성 요소에서는 런타임 연결에 지정된 연결 관리자에 대한 연결을 설정한 후 외부 데이터 원본에 대한 연결을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-122">The component should establish a connection to the connection manager specified by the run-time connection, and subsequently, to the external data source.</span></span>

 <span data-ttu-id="aa1d1-123">연결이 설정되면 구성 요소에서는 연결을 내부에 캐시했다가 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 메서드가 호출되면 이를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-123">After the connection is established, it should be cached internally by the component and released when the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method is called.</span></span> <span data-ttu-id="aa1d1-124"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 메서드는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 메서드와 마찬가지로 디자인 및 실행 중에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-124">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method is called at design and execution time, like the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method.</span></span> <span data-ttu-id="aa1d1-125">개발자는 이 메서드를 재정의하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 실행 중에 구성 요소에서 설정한 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-125">Developers override this method, and release the connection established by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span>

 <span data-ttu-id="aa1d1-126">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 메서드에서 ADO.NET 연결에 연결한 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 메서드에서 연결을 닫는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-126">The following code example shows a component that connects to an ADO.NET connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method and closes the connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method.</span></span>

```csharp
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
Private sqlConnection As SqlConnection

Public Overrides Sub AcquireConnections(ByVal transaction As Object)

    If Not IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) Then

        Dim cm As ConnectionManager = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject, ConnectionManagerAdoNet)

        If IsNothing(cmado) Then
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")
        End If

        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)
        sqlConnection.Open()

    End If
End Sub

Public Overrides Sub ReleaseConnections()

    If Not IsNothing(sqlConnection) And sqlConnection.State <> ConnectionState.Closed Then
        sqlConnection.Close()
    End If

End Sub
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="aa1d1-127">출력 열 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="aa1d1-127">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="aa1d1-128">원본 구성 요소의 출력 열은 실행 중 구성 요소에서 데이터 흐름에 추가하는 외부 데이터 원본의 열을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-128">The output columns of a source component reflect the columns from the external data source that the component adds to the data flow during execution.</span></span> <span data-ttu-id="aa1d1-129">디자인 타임에는 구성 요소가 외부 데이터 원본에 연결하도록 구성된 후 출력 열을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-129">At design time, you add output columns after the component has been configured to connect to an external data source.</span></span> <span data-ttu-id="aa1d1-130">구성 요소에서 출력 컬렉션에 열을 추가하는 데 사용하는 디자인 타임 메서드는 구성 요소의 요구 사항에 따라 달라질 수 있지만 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 또는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 실행 중에는 디자인 타임 메서드를 추가하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-130">The design-time method that a component uses to add the columns to its output collection can vary based on the needs of the component, although they should not be added during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span> <span data-ttu-id="aa1d1-131">예를 들어 구성 요소의 데이터 집합을 제어하는 사용자 지정 속성에서 SQL 문이 포함된 구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A> 메서드 실행 중 출력 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-131">For example, a component that contains a SQL statement in a custom property that controls the data set for the component may add its output columns during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A> method.</span></span> <span data-ttu-id="aa1d1-132">구성 요소에서는 캐시된 연결이 있는지 여부를 확인하고, 캐시된 연결이 있으면 데이터 원본에 연결하여 출력 열을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-132">The component checks to see whether it has a cached connection, and, if it does, connects to the data source and generates its output columns.</span></span>

 <span data-ttu-id="aa1d1-133">출력 열이 만들어진 후에는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> 메서드를 호출하여 해당 데이터 형식 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-133">After an output column has been created, set its data type properties by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="aa1d1-134"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> 속성은 읽기 전용이고 각기 다른 속성의 설정에 따라 달라지므로 이 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-134">This method is necessary because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are read-only and each property is dependent on the settings of the other.</span></span> <span data-ttu-id="aa1d1-135">이 메서드는 이러한 값이 일관성 있게 설정되도록 하며 데이터 흐름 태스크에서는 해당 값이 올바르게 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-135">This method enforces the need for these values to be set consistently, and the data flow task validates that they are set correctly.</span></span>

 <span data-ttu-id="aa1d1-136">열의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>은 다른 속성에 대해 설정되는 값을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="aa1d1-137">다음 표에서는 각 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>의 종속 속성에 대한 요구 사항을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-137">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="aa1d1-138">이 목록에 포함되지 않은 데이터 형식의 종속 속성은 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-138">The data types not listed have their dependent properties set to zero.</span></span>

|<span data-ttu-id="aa1d1-139">DataType</span><span class="sxs-lookup"><span data-stu-id="aa1d1-139">DataType</span></span>|<span data-ttu-id="aa1d1-140">길이</span><span class="sxs-lookup"><span data-stu-id="aa1d1-140">Length</span></span>|<span data-ttu-id="aa1d1-141">확장</span><span class="sxs-lookup"><span data-stu-id="aa1d1-141">Scale</span></span>|<span data-ttu-id="aa1d1-142">자릿수</span><span class="sxs-lookup"><span data-stu-id="aa1d1-142">Precision</span></span>|<span data-ttu-id="aa1d1-143">CodePage</span><span class="sxs-lookup"><span data-stu-id="aa1d1-143">CodePage</span></span>|
|--------------|------------|-----------|---------------|--------------|
|<span data-ttu-id="aa1d1-144">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="aa1d1-144">DT_DECIMAL</span></span>|<span data-ttu-id="aa1d1-145">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-145">0</span></span>|<span data-ttu-id="aa1d1-146">0보다 크고 28보다 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-146">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="aa1d1-147">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-147">0</span></span>|<span data-ttu-id="aa1d1-148">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-148">0</span></span>|
|<span data-ttu-id="aa1d1-149">DT_CY</span><span class="sxs-lookup"><span data-stu-id="aa1d1-149">DT_CY</span></span>|<span data-ttu-id="aa1d1-150">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-150">0</span></span>|<span data-ttu-id="aa1d1-151">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-151">0</span></span>|<span data-ttu-id="aa1d1-152">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-152">0</span></span>|<span data-ttu-id="aa1d1-153">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-153">0</span></span>|
|<span data-ttu-id="aa1d1-154">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="aa1d1-154">DT_NUMERIC</span></span>|<span data-ttu-id="aa1d1-155">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-155">0</span></span>|<span data-ttu-id="aa1d1-156">0보다 크고 28보다 작거나 같으며 Precision보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-156">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="aa1d1-157">1보다 크거나 같고 38보다 작거나 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-157">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="aa1d1-158">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-158">0</span></span>|
|<span data-ttu-id="aa1d1-159">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="aa1d1-159">DT_BYTES</span></span>|<span data-ttu-id="aa1d1-160">0보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-160">Greater than 0.</span></span>|<span data-ttu-id="aa1d1-161">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-161">0</span></span>|<span data-ttu-id="aa1d1-162">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-162">0</span></span>|<span data-ttu-id="aa1d1-163">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-163">0</span></span>|
|<span data-ttu-id="aa1d1-164">DT_STR</span><span class="sxs-lookup"><span data-stu-id="aa1d1-164">DT_STR</span></span>|<span data-ttu-id="aa1d1-165">0보다 크고 8000보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-165">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="aa1d1-166">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-166">0</span></span>|<span data-ttu-id="aa1d1-167">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-167">0</span></span>|<span data-ttu-id="aa1d1-168">0이 아니며 올바른 코드 페이지가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-168">Not 0, and a valid code page.</span></span>|
|<span data-ttu-id="aa1d1-169">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="aa1d1-169">DT_WSTR</span></span>|<span data-ttu-id="aa1d1-170">0보다 크고 4000보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-170">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="aa1d1-171">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-171">0</span></span>|<span data-ttu-id="aa1d1-172">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-172">0</span></span>|<span data-ttu-id="aa1d1-173">0</span><span class="sxs-lookup"><span data-stu-id="aa1d1-173">0</span></span>|

 <span data-ttu-id="aa1d1-174">데이터 형식 속성에 대한 제한 사항은 출력 열의 데이터 형식을 기준으로 하므로 관리되는 형식을 사용할 때는 올바른 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-174">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="aa1d1-175">기본 클래스는 관리되는 구성 요소 개발자가 관리되는 형식이 지정된 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식을 선택하는 데 도움이 되는 세 개의 도우미 메서드(<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-175">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>, to assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="aa1d1-176">이러한 메서드는 관리되는 데이터 형식을 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 데이터 형식으로 변환하거나 그 반대로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-176">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>

 <span data-ttu-id="aa1d1-177">다음 코드 예에서는 테이블의 스키마를 기반으로 구성 요소의 출력 열 컬렉션을 채우는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-177">The following code example shows how the output column collection of a component is populated based on the schema of a table.</span></span> <span data-ttu-id="aa1d1-178">기본 클래스의 도우미 메서드는 열의 데이터 형식을 설정하는 데 사용되며 종속 속성은 해당 데이터 형식에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-178">The helper methods of the base class are used to set the data type of the column, and the dependent properties are set based on the data type.</span></span>

```csharp
SqlCommand sqlCommand;

private void CreateColumnsFromDataTable()
{
    // Get the output.
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

    // Start clean, and remove the columns from both collections.
    output.OutputColumnCollection.RemoveAll();
    output.ExternalMetadataColumnCollection.RemoveAll();

    this.sqlCommand = sqlConnection.CreateCommand();
    this.sqlCommand.CommandType = CommandType.Text;
    this.sqlCommand.CommandText = (string)ComponentMetaData.CustomPropertyCollection["SqlStatement"].Value;
    SqlDataReader schemaReader = this.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly);
    DataTable dataTable = schemaReader.GetSchemaTable();

    // Walk the columns in the schema, 
    // and for each data column create an output column and an external metadata column.
    foreach (DataRow row in dataTable.Rows)
    {
        IDTSOutputColumn100 outColumn = output.OutputColumnCollection.New();
        IDTSExternalMetadataColumn100 exColumn = output.ExternalMetadataColumnCollection.New();

        // Set column data type properties.
        bool isLong = false;
        DataType dt = DataRecordTypeToBufferType((Type)row["DataType"]);
        dt = ConvertBufferDataTypeToFitManaged(dt, ref isLong);
        int length = 0;
        int precision = (short)row["NumericPrecision"];
        int scale = (short)row["NumericScale"];
        int codepage = dataTable.Locale.TextInfo.ANSICodePage;

        switch (dt)
        {
            // The length cannot be zero, and the code page property must contain a valid code page.
            case DataType.DT_STR:
            case DataType.DT_TEXT:
                length = precision;
                precision = 0;
                scale = 0;
                break;

            case DataType.DT_WSTR:
                length = precision;
                codepage = 0;
                scale = 0;
                precision = 0;
                break;

            case DataType.DT_BYTES:
                precision = 0;
                scale = 0;
                codepage = 0;
                break;

            case DataType.DT_NUMERIC:
                length = 0;
                codepage = 0;

                if (precision > 38)
                    precision = 38;

                if (scale > 6)
                    scale = 6;
                break;

            case DataType.DT_DECIMAL:
                length = 0;
                precision = 0;
                codepage = 0;
                break;

            default:
                length = 0;
                precision = 0;
                codepage = 0;
                scale = 0;
                break;

        }

        // Set the properties of the output column.
        outColumn.Name = (string)row["ColumnName"];
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage);
    }
}
```

```vb
Private sqlCommand As SqlCommand

Private Sub CreateColumnsFromDataTable()

    ' Get the output.
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

    ' Start clean, and remove the columns from both collections.
    output.OutputColumnCollection.RemoveAll()
    output.ExternalMetadataColumnCollection.RemoveAll()

    Me.sqlCommand = sqlConnection.CreateCommand()
    Me.sqlCommand.CommandType = CommandType.Text
    Me.sqlCommand.CommandText = CStr(ComponentMetaData.CustomPropertyCollection("SqlStatement").Value)

    Dim schemaReader As SqlDataReader = Me.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly)
    Dim dataTable As DataTable = schemaReader.GetSchemaTable()

    ' Walk the columns in the schema, 
    ' and for each data column create an output column and an external metadata column.
    For Each row As DataRow In dataTable.Rows

        Dim outColumn As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        Dim exColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()

        ' Set column data type properties.
        Dim isLong As Boolean = False
        Dim dt As DataType = DataRecordTypeToBufferType(CType(row("DataType"), Type))
        dt = ConvertBufferDataTypeToFitManaged(dt, isLong)
        Dim length As Integer = 0
        Dim precision As Integer = CType(row("NumericPrecision"), Short)
        Dim scale As Integer = CType(row("NumericScale"), Short)
        Dim codepage As Integer = dataTable.Locale.TextInfo.ANSICodePage

        Select Case dt

            ' The length cannot be zero, and the code page property must contain a valid code page.
            Case DataType.DT_STR
            Case DataType.DT_TEXT
                length = precision
                precision = 0
                scale = 0

            Case DataType.DT_WSTR
                length = precision
                codepage = 0
                scale = 0
                precision = 0

            Case DataType.DT_BYTES
                precision = 0
                scale = 0
                codepage = 0

            Case DataType.DT_NUMERIC
                length = 0
                codepage = 0

                If precision > 38 Then
                    precision = 38
                End If

                If scale > 6 Then
                    scale = 6
                End If

            Case DataType.DT_DECIMAL
                length = 0
                precision = 0
                codepage = 0

            Case Else
                length = 0
                precision = 0
                codepage = 0
                scale = 0
        End Select

        ' Set the properties of the output column.
        outColumn.Name = CStr(row("ColumnName"))
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage)
    Next
End Sub
```

### <a name="validating-the-component"></a><span data-ttu-id="aa1d1-179">구성 요소 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="aa1d1-179">Validating the Component</span></span>
 <span data-ttu-id="aa1d1-180">원본 구성 요소의 유효성을 검사하고 해당 출력 열 컬렉션에 정의된 열과 외부 데이터 원본에 있는 열이 일치하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-180">You should validate a source component and verify that the columns defined in its output column collections match the columns at the external data source.</span></span> <span data-ttu-id="aa1d1-181">때로는 연결이 끊어진 상태이거나 오랜 서버 왕복을 피하는 것이 바람직할 때와 같이 외부 데이터 원본을 기준으로 출력 열의 유효성을 검사하는 것이 불가능한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-181">Sometimes, verifying the output columns against the external data source can be impossible, such as in a disconnected state, or when it is preferable to avoid lengthy round trips to the server.</span></span> <span data-ttu-id="aa1d1-182">이러한 경우에도 출력 개체의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A>을 사용하여 출력의 열에 대한 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-182">In these situations, the columns in the output can still be validated by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A> of the output object.</span></span> <span data-ttu-id="aa1d1-183">자세한 내용은 [데이터 흐름 구성 요소에 대한 유효성 검사](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-183">For more information, see [Validating a Data Flow Component](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md).</span></span>

 <span data-ttu-id="aa1d1-184">이 컬렉션은 입력 개체와 출력 개체 모두에 있으며 외부 데이터 원본의 열로 이 컬렉션을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-184">This collection exists on both input and output objects and you can populate it with the columns from the external data source.</span></span> <span data-ttu-id="aa1d1-185">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너가 오프라인 상태이거나 구성 요소의 연결이 끊어져 있거나 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 속성이 `false`인 경우 이 컬렉션을 사용하여 출력 열의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-185">You can use this collection to validate the output columns when [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is offline, when the component is disconnected, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span> <span data-ttu-id="aa1d1-186">먼저 출력 열이 만들어짐과 동시에 컬렉션이 채워져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-186">The collection should be first populated at the same time that the output columns are created.</span></span> <span data-ttu-id="aa1d1-187">외부 메타데이터 열은 처음에는 출력 열과 일치하므로 컬렉션에 외부 메타데이터 열을 추가하는 것은 비교적 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-187">Adding external metadata columns to the collection is relatively easy because the external metadata column should initially match the output column.</span></span> <span data-ttu-id="aa1d1-188">열의 데이터 형식 속성은 이미 올바르게 설정되어 있어야 하며 이 속성을 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> 개체에 직접 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-188">The data type properties of the column should have already been set correctly, and the properties can be copied directly to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> object.</span></span>

 <span data-ttu-id="aa1d1-189">다음 예제 코드에서는 새로 만들어진 출력 열을 기반으로 외부 메타데이터 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-189">The following sample code adds an external metadata column that is based on a newly created output column.</span></span> <span data-ttu-id="aa1d1-190">출력 열은 이미 만들어진 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-190">It assumes that the output column has already been created.</span></span>

```csharp
private void CreateExternalMetaDataColumn(IDTSOutput100 output, IDTSOutputColumn100 outputColumn)
{

    // Set the properties of the external metadata column.
    IDTSExternalMetadataColumn100 externalColumn = output.ExternalMetadataColumnCollection.New();
    externalColumn.Name = outputColumn.Name;
    externalColumn.Precision = outputColumn.Precision;
    externalColumn.Length = outputColumn.Length;
    externalColumn.DataType = outputColumn.DataType;
    externalColumn.Scale = outputColumn.Scale;

    // Map the external column to the output column.
    outputColumn.ExternalMetadataColumnID = externalColumn.ID;

}
```

```vb
Private Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumn As IDTSOutputColumn100)

        ' Set the properties of the external metadata column.
        Dim externalColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()
        externalColumn.Name = outputColumn.Name
        externalColumn.Precision = outputColumn.Precision
        externalColumn.Length = outputColumn.Length
        externalColumn.DataType = outputColumn.DataType
        externalColumn.Scale = outputColumn.Scale

        ' Map the external column to the output column.
        outputColumn.ExternalMetadataColumnID = externalColumn.ID

    End Sub
```

## <a name="run-time"></a><span data-ttu-id="aa1d1-191">런타임</span><span class="sxs-lookup"><span data-stu-id="aa1d1-191">Run Time</span></span>
 <span data-ttu-id="aa1d1-192">실행 중 구성 요소는 데이터 흐름 태스크에서 만들어 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>을 통해 구성 요소에 제공한 출력 버퍼에 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-192">During execution, components add rows to output buffers that are created by the data flow task and provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span> <span data-ttu-id="aa1d1-193">원본 구성 요소에 대해 이 메서드가 호출되고 나면 이 메서드는 다운스트림 구성 요소에 연결된 구성 요소의 각 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>에 대한 출력 버퍼를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-193">Called once for source components, the method receives an output buffer for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the component that is connected to a downstream component.</span></span>

### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="aa1d1-194">버퍼에서 열 찾기</span><span class="sxs-lookup"><span data-stu-id="aa1d1-194">Locating Columns in the Buffer</span></span>
 <span data-ttu-id="aa1d1-195">구성 요소의 출력 버퍼에는 해당 구성 요소에서 정의한 열과 다운스트림 구성 요소의 출력에 추가된 열이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-195">The output buffer for a component contains the columns defined by the component and any columns added to the output of a downstream component.</span></span> <span data-ttu-id="aa1d1-196">예를 들어 원본 구성 요소에서 출력에 세 개의 열을 제공하고 다음 구성 요소에서 네 번째 출력 열을 하나 추가할 경우, 원본 구성 요소에서 사용하도록 제공된 출력 버퍼에는 이 네 개의 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-196">For example, if a source component provides three columns in its output, and the next component adds a fourth output column, the output buffer provided for use by the source component contains these four columns.</span></span>

 <span data-ttu-id="aa1d1-197">버퍼 행의 열 순서는 출력 열 컬렉션에 있는 출력 열의 인덱스로 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-197">The order of the columns in a buffer row is not defined by the index of the output column in the output column collection.</span></span> <span data-ttu-id="aa1d1-198">따라서 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 메서드를 사용해야 버퍼 행에서 출력 열을 정확하게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-198">An output column can only be accurately located in a buffer row by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="aa1d1-199">이 메서드는 지정된 버퍼에서 지정된 계보 ID가 있는 열을 찾고 해당 위치를 행에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-199">This method locates the column with the specified lineage ID in the specified buffer, and returns its location in the row.</span></span> <span data-ttu-id="aa1d1-200">출력 열의 인덱스는 일반적으로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 메서드 실행 중에 검색되며 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 실행 중에 사용할 수 있도록 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-200">The indexes of the output columns are typically located in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, and stored for use during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span>

 <span data-ttu-id="aa1d1-201">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>를 호출하는 중에 출력 버퍼에서 출력 열의 위치를 찾고 이를 내부 구조에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-201">The following code example finds the location of the output columns in the output buffer during a call to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, and stores them in an internal structure.</span></span> <span data-ttu-id="aa1d1-202">열의 이름도 구조에 저장되며 이 이름은 이 항목의 다음 섹션에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 메서드에 대한 코드 예에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-202">The name of the column is also stored in the structure and is used in the code example for the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method in the next section of this topic.</span></span>

```csharp
ArrayList columnInformation;

private struct ColumnInfo
{
    public int BufferColumnIndex;
    public string ColumnName;
}

public override void PreExecute()
{
    this.columnInformation = new ArrayList();
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

    foreach (IDTSOutputColumn100 col in output.OutputColumnCollection)
    {
        ColumnInfo ci = new ColumnInfo();
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID);
        ci.ColumnName = col.Name;
        columnInformation.Add(ci);
    }
}
```

```vb
Public Overrides Sub PreExecute()

    Me.columnInformation = New ArrayList()
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

    For Each col As IDTSOutputColumn100 In output.OutputColumnCollection

        Dim ci As ColumnInfo = New ColumnInfo()
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID)
        ci.ColumnName = col.Name
        columnInformation.Add(ci)
    Next
End Sub
```

### <a name="processing-rows"></a><span data-ttu-id="aa1d1-203">행 처리</span><span class="sxs-lookup"><span data-stu-id="aa1d1-203">Processing Rows</span></span>
 <span data-ttu-id="aa1d1-204"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> 메서드를 호출하여 출력 버퍼에 행을 추가하면 열에 빈 값이 있는 새 버퍼 행이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-204">Rows are added to the output buffer by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method, which creates a new buffer row with empty values in its columns.</span></span> <span data-ttu-id="aa1d1-205">그런 다음 구성 요소에서는 개별 열에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-205">The component then assigns values to the individual columns.</span></span> <span data-ttu-id="aa1d1-206">구성 요소에 제공된 출력 버퍼는 데이터 흐름 태스크에서 만들어지고 모니터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-206">The output buffers provided to a component are created and monitored by the data flow task.</span></span> <span data-ttu-id="aa1d1-207">출력 버퍼가 가득 차면 버퍼의 행은 다음 구성 요소로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-207">As they become full, the rows in the buffer are moved to the next component.</span></span> <span data-ttu-id="aa1d1-208">데이터 흐름 태스크에 의한 행 이동은 구성 요소 개발자가 인식할 수 있으며 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> 속성은 출력 버퍼에서 항상 0으로 설정되므로 행 일괄 처리가 다음 구성 요소로 보내졌는지 확인할 수 있는 방법은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-208">There is no way to determine when a batch of rows has been sent to the next component because the movement of rows by the data flow task is transparent to the component developer, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> property is always zero on output buffers.</span></span> <span data-ttu-id="aa1d1-209">출력 버퍼에 행을 모두 추가한 경우 원본 구성 요소에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 메서드를 호출하여 이를 데이터 흐름 태스크에 알리며 버퍼의 나머지 행은 다음 구성 요소에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-209">When a source component is finished adding rows to its output buffer, it notifies the data flow task by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, and the remaining rows in the buffer are passed to the next component.</span></span>

 <span data-ttu-id="aa1d1-210">원본 구성 요소에서 외부 데이터 원본의 행을 읽는 동안 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> 메서드를 호출하여 "Rows read" 또는 "BLOB bytes read" 성능 카운터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-210">While the source component reads rows from the external data source, you may want to update the "Rows read" or "BLOB bytes read" performance counters by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> method.</span></span> <span data-ttu-id="aa1d1-211">자세한 내용은 [성능 카운터](../performance/performance-counters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-211">For more information, see [Performance Counters](../performance/performance-counters.md).</span></span>

 <span data-ttu-id="aa1d1-212">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>에서 출력 버퍼에 행을 추가하는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-212">The following code example shows a component that adds rows to an output buffer in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span> <span data-ttu-id="aa1d1-213">버퍼에 있는 출력 열의 인덱스는 위의 코드 예에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 사용 중 찾은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-213">The indexes of the output columns in the buffer were located using <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> in the previous code example.</span></span>

```csharp
public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
{
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
    PipelineBuffer buffer = buffers[0];

    SqlDataReader dataReader = sqlCommand.ExecuteReader();

    // Loop over the rows in the DataReader, 
    // and add them to the output buffer.
    while (dataReader.Read())
    {
        // Add a row to the output buffer.
        buffer.AddRow();

        for (int x = 0; x < columnInformation.Count; x++)
        {
            ColumnInfo ci = (ColumnInfo)columnInformation[x];
            int ordinal = dataReader.GetOrdinal(ci.ColumnName);

            if (dataReader.IsDBNull(ordinal))
                buffer.SetNull(ci.BufferColumnIndex);
            else
            {
                buffer[ci.BufferColumnIndex] = dataReader[ci.ColumnName];
            }
        }
    }
    buffer.SetEndOfRowset();
}
```

```vb
Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim buffer As PipelineBuffer = buffers(0)

    Dim dataReader As SqlDataReader = sqlCommand.ExecuteReader()

    ' Loop over the rows in the DataReader, 
    ' and add them to the output buffer.
    While (dataReader.Read())

        ' Add a row to the output buffer.
        buffer.AddRow()

        For x As Integer = 0 To columnInformation.Count

            Dim ci As ColumnInfo = CType(columnInformation(x), ColumnInfo)

            Dim ordinal As Integer = dataReader.GetOrdinal(ci.ColumnName)

            If (dataReader.IsDBNull(ordinal)) Then
                buffer.SetNull(ci.BufferColumnIndex)
            Else
                buffer(ci.BufferColumnIndex) = dataReader(ci.ColumnName)

            End If
        Next

    End While

    buffer.SetEndOfRowset()
End Sub
```

## <a name="sample"></a><span data-ttu-id="aa1d1-214">샘플</span><span class="sxs-lookup"><span data-stu-id="aa1d1-214">Sample</span></span>
 <span data-ttu-id="aa1d1-215">다음 예제에서는 파일 연결 관리자를 사용하여 파일의 이진 내용을 데이터 흐름으로 로드하는 간단한 원본 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-215">The following sample shows a simple source component that uses a File connection manager to load the binary contents of files into the data flow.</span></span> <span data-ttu-id="aa1d1-216">이 예제는 이 항목에 설명된 메서드 및 기능의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-216">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="aa1d1-217">또한 모든 사용자 지정 원본 구성 요소에서 재정의해야 하는 중요한 메서드를 보여 주지만 디자인 타임 유효성 검사를 위한 코드는 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-217">It demonstrates the important methods that every custom source component must override, but does not contain code for design-time validation.</span></span>

```csharp
using System;
using System.IO;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace BlobSrc
{
  [DtsPipelineComponent(DisplayName = "BLOB Inserter Source", Description = "Inserts files into the data flow as BLOBs")]
  public class BlobSrc : PipelineComponent
  {
    IDTSConnectionManager100 m_ConnMgr;
    int m_FileNameColumnIndex = -1;
    int m_FileBlobColumnIndex = -1;

    public override void ProvideComponentProperties()
    {
      IDTSOutput100 output = ComponentMetaData.OutputCollection.New();
      output.Name = "BLOB File Inserter Output";

      IDTSOutputColumn100 column = output.OutputColumnCollection.New();
      column.Name = "FileName";
      column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0);

      column = output.OutputColumnCollection.New();
      column.Name = "FileBLOB";
      column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0);

      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();
      conn.Name = "FileConnection";
    }

    public override void AcquireConnections(object transaction)
    {
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];
      m_ConnMgr = conn.ConnectionManager;
    }

    public override void ReleaseConnections()
    {
      m_ConnMgr = null;
    }

    public override void PreExecute()
    {
      IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

      m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[0].LineageID);
      m_FileBlobColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[1].LineageID);
    }

    public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
    {
      string strFileName = (string)m_ConnMgr.AcquireConnection(null);

      while (strFileName != null)
      {
        buffers[0].AddRow();

        buffers[0].SetString(m_FileNameColumnIndex, strFileName);

        FileInfo fileInfo = new FileInfo(strFileName);
        byte[] fileData = new byte[fileInfo.Length];
        FileStream fs = new FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read);
        fs.Read(fileData, 0, fileData.Length);

        buffers[0].AddBlobData(m_FileBlobColumnIndex, fileData);

        strFileName = (string)m_ConnMgr.AcquireConnection(null);
      }

      buffers[0].SetEndOfRowset();
    }
  }
}
```

```vb
Imports System 
Imports System.IO 
Imports Microsoft.SqlServer.Dts.Pipeline 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper 
Namespace BlobSrc 

 <DtsPipelineComponent(DisplayName="BLOB Inserter Source", Description="Inserts files into the data flow as BLOBs")> _ 
 Public Class BlobSrc 
 Inherits PipelineComponent 
   Private m_ConnMgr As IDTSConnectionManager100 
   Private m_FileNameColumnIndex As Integer = -1 
   Private m_FileBlobColumnIndex As Integer = -1 

   Public  Overrides Sub ProvideComponentProperties() 
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New 
     output.Name = "BLOB File Inserter Output" 
     Dim column As IDTSOutputColumn100 = output.OutputColumnCollection.New 
     column.Name = "FileName" 
     column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0) 
     column = output.OutputColumnCollection.New 
     column.Name = "FileBLOB" 
     column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0) 
     Dim conn As IDTSRuntimeConnection90 = ComponentMetaData.RuntimeConnectionCollection.New 
     conn.Name = "FileConnection" 
   End Sub 

   Public  Overrides Sub AcquireConnections(ByVal transaction As Object) 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0) 
     m_ConnMgr = conn.ConnectionManager 
   End Sub 

   Public  Overrides Sub ReleaseConnections() 
     m_ConnMgr = Nothing 
   End Sub 

   Public  Overrides Sub PreExecute() 
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0) 
     m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(0).LineageID), Integer) 
     m_FileBlobColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(1).LineageID), Integer) 
   End Sub 

   Public  Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer()) 
     Dim strFileName As String = CType(m_ConnMgr.AcquireConnection(Nothing), String) 
     While Not (strFileName Is Nothing) 
       buffers(0).AddRow 
       buffers(0).SetString(m_FileNameColumnIndex, strFileName) 
       Dim fileInfo As FileInfo = New FileInfo(strFileName) 
       Dim fileData(fileInfo.Length) As Byte 
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read) 
       fs.Read(fileData, 0, fileData.Length) 
       buffers(0).AddBlobData(m_FileBlobColumnIndex, fileData) 
       strFileName = CType(m_ConnMgr.AcquireConnection(Nothing), String) 
     End While 
     buffers(0).SetEndOfRowset 
   End Sub 
 End Class 
End Namespace
```

<span data-ttu-id="aa1d1-218">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="aa1d1-218">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="aa1d1-219">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-219">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="aa1d1-220">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-220">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="aa1d1-221">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="aa1d1-221">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa1d1-222">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa1d1-222">See Also</span></span>
 <span data-ttu-id="aa1d1-223">[사용자 지정 대상 구성 요소 개발](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) [스크립트 구성 요소를 사용 하 여 원본 만들기](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="aa1d1-223">[Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) [Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)</span></span>


