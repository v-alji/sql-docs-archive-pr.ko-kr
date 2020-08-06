---
title: 프로그래밍 방식으로 데이터 흐름 구성 요소 추가 | Microsoft Docs
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
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: c06065cf-43e5-4b6b-9824-7309d7f5e35e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 807e758e42b738c4b0bf64b1d6f48bc29649ae6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649648"
---
# <a name="adding-data-flow-components-programmatically"></a><span data-ttu-id="d1e29-102">프로그래밍 방식으로 데이터 흐름 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="d1e29-102">Adding Data Flow Components Programmatically</span></span>
  <span data-ttu-id="d1e29-103">데이터 흐름을 작성할 때는 먼저 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-103">When you build a data flow, you start by adding components.</span></span> <span data-ttu-id="d1e29-104">그런 다음 해당 구성 요소를 구성하고 서로 연결하여 런타임에 데이터의 흐름을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-104">Then you configure those components and connect them together to establish the flow of data at run time.</span></span> <span data-ttu-id="d1e29-105">이 섹션에서는 데이터 흐름 태스크에 구성 요소를 추가하고 해당 구성 요소의 디자인 타임 인스턴스를 만든 다음 구성 요소를 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-105">This section describes adding a component to the data flow task, creating the design-time instance of the component, and then configuring the component.</span></span> <span data-ttu-id="d1e29-106">구성 요소를 연결하는 방법에 대한 자세한 내용은 [프로그래밍 방식으로 데이터 흐름 구성 요소 연결](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e29-106">For information about how to connect components, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-component"></a><span data-ttu-id="d1e29-107">구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="d1e29-107">Adding a Component</span></span>  
 <span data-ttu-id="d1e29-108"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> 메서드를 호출하여 새 구성 요소를 만들고 이를 데이터 흐름 태스크에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> collection to create a new component and add it to the data flow task.</span></span> <span data-ttu-id="d1e29-109">이 메서드는 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-109">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component.</span></span> <span data-ttu-id="d1e29-110">하지만 이 시점에서 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>에는 구성 요소와 관련된 정보가 들어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-110">However, at this point, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> does not contain information specific to any one component.</span></span> <span data-ttu-id="d1e29-111">구성 요소의 형식을 식별하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-111">Set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property to identify the type of component.</span></span> <span data-ttu-id="d1e29-112">데이터 흐름 태스크에서는 런타임에 이 속성 값을 사용하여 구성 요소의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-112">The data flow task uses the value of this property to create an instance of the component at run time.</span></span>  
  
 <span data-ttu-id="d1e29-113"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 속성에 지정된 값은 CLSID, PROGID 또는 구성 요소의 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 속성일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-113">The value specified in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property can be the CLSID, PROGID, or <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property of the component.</span></span> <span data-ttu-id="d1e29-114">CLSID는 일반적으로 속성 창에서 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 속성 값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-114">The CLSID is normally displayed in the Properties window as the value of the component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="d1e29-115">이 속성과 사용 가능한 구성 요소의 다른 속성을 가져오는 방법은 [프로그래밍 방식으로 데이터 흐름 구성 요소 검색](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e29-115">For information about obtaining this property and other properties of available components, see [Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-managed-component"></a><span data-ttu-id="d1e29-116">관리되는 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="d1e29-116">Adding a Managed Component</span></span>  
 <span data-ttu-id="d1e29-117">CLSID나 PROGID는 구성 요소 자체가 아니라 래퍼를 가리키므로 이러한 값을 사용하여 데이터 흐름에 관리되는 데이터 흐름 구성 요소를 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-117">You cannot use the CLSID or PROGID to add one the managed data flow components to the data flow, because these values point to a wrapper and not to the component itself.</span></span> <span data-ttu-id="d1e29-118">대신 다음 예제에 표시된 대로 `CreationName` 속성이나 `AssemblyQualifiedName` 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-118">Instead you can use the `CreationName` property or the `AssemblyQualifiedName` property as shown in the following sample.</span></span>  
  
 <span data-ttu-id="d1e29-119">`AssemblyQualifiedName` 속성을 사용하려면 관리되는 구성 요소가 들어 있는 어셈블리에 대한 참조를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-119">If you intend to use the `AssemblyQualifiedName` property, then you must add a reference in your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] project to the assembly that contains the managed component.</span></span> <span data-ttu-id="d1e29-120">이러한 어셈블리는 **참조 추가** 대화 상자의 .NET 탭에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-120">These assemblies are not listed on the .NET tab of the **Add Reference** dialog box.</span></span> <span data-ttu-id="d1e29-121">일반적으로 **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** 폴더의 어셈블리를 찾도록 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-121">Normally you must browse to locate the assembly in the **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** folder.</span></span>  
  
 <span data-ttu-id="d1e29-122">기본 제공되는 관리되는 데이터 흐름 구성 요소에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-122">The built-in managed data flow components include:</span></span>  
  
-   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="d1e29-123">원본</span><span class="sxs-lookup"><span data-stu-id="d1e29-123">Source</span></span>  
  
-   <span data-ttu-id="d1e29-124">XML 원본</span><span class="sxs-lookup"><span data-stu-id="d1e29-124">XML Source</span></span>  
  
-   <span data-ttu-id="d1e29-125">DataReader 대상</span><span class="sxs-lookup"><span data-stu-id="d1e29-125">DataReader Destination</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1e29-126">Compact 대상</span><span class="sxs-lookup"><span data-stu-id="d1e29-126">Compact Destination</span></span>  
  
-   <span data-ttu-id="d1e29-127">스크립트 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d1e29-127">Script Component</span></span>  
  
 <span data-ttu-id="d1e29-128">다음 코드 예제에서는 데이터 흐름에 관리되는 구성 요소를 추가하는 두 가지 방법을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-128">The following code sample shows both ways of adding a managed component to the data flow:</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Microsoft.SqlServer.Dts.Runtime.Package package = new Microsoft.SqlServer.Dts.Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Microsoft.SqlServer.Dts.Runtime.TaskHost thMainPipe = (Microsoft.SqlServer.Dts.Runtime.TaskHost)e;  
      MainPipe dataFlowTask = (MainPipe)thMainPipe.InnerObject;  
  
      // The Application object will be used to obtain the CreationName  
      //  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
      Application app = new Application();  
  
      // Add a first ADO NET source to the data flow.  
      //  The CreationName property requires an Application instance.  
      IDTSComponentMetaData100 component1 = dataFlowTask.ComponentMetaDataCollection.New();  
      component1.Name = "DataReader Source";  
      component1.ComponentClassID = app.PipelineComponentInfos["DataReader Source"].CreationName;  
  
      // Add a second ADO NET source to the data flow.  
      //  The AssemblyQualifiedName property requires a reference to the assembly.  
      IDTSComponentMetaData100 component2 = dataFlowTask.ComponentMetaDataCollection.New();  
      component2.Name = "DataReader Source";  
      component2.ComponentClassID = typeof(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName;  
    }  
  }  
}  
  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' The Application object will be used to obtain the CreationName  
    '  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
    Dim app As New Application()  
  
    ' Add a first ADO NET source to the data flow.  
    '  The CreationName property requires an Application instance.  
    Dim component1 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component1.Name = "DataReader Source"  
    component1.ComponentClassID = app.PipelineComponentInfos("DataReader Source").CreationName  
  
    ' Add a second ADO NET source to the data flow.  
    '  The AssemblyQualifiedName property requires a reference to the assembly.  
    Dim component2 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component2.Name = "DataReader Source"  
    component2.ComponentClassID = _  
      GetType(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName  
  
  End Sub  
  
End Module  
```  
  
## <a name="creating-the-design-time-instance-of-the-component"></a><span data-ttu-id="d1e29-129">구성 요소의 디자인 타임 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="d1e29-129">Creating the Design-time Instance of the Component</span></span>  
 <span data-ttu-id="d1e29-130"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> 메서드를 호출하여 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 속성으로 식별된 구성 요소의 디자인 타임 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-130">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method to create the design time instance of the component identified by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="d1e29-131">이 메서드는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 인터페이스의 관리되는 래퍼인 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-131">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> object, which is the managed wrapper for the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="d1e29-132">가능하면 항상 구성 요소 메타데이터를 직접 수정하는 대신 디자인 타임 인스턴스의 메서드를 사용하여 구성 요소를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-132">Whenever possible, you should modify a component by using the methods of the design-time instance instead of by modifying the component metadata directly.</span></span> <span data-ttu-id="d1e29-133">메타데이터에는 연결과 같이 직접 설정해야 하는 항목도 있지만 일반적으로 메타데이터를 직접 수정할 경우에는 구성 요소의 변경 내용 모니터링 및 유효성 검사 기능을 사용할 수 없으므로 이 방법은 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-133">Although there are items in the metadata that you must set directly, such as connections, generally it is inadvisable to modify the metadata directly because you bypass the ability of the component to monitor and validate changes.</span></span>  
  
## <a name="assigning-connections"></a><span data-ttu-id="d1e29-134">연결 할당</span><span class="sxs-lookup"><span data-stu-id="d1e29-134">Assigning Connections</span></span>  
 <span data-ttu-id="d1e29-135">OLE DB 원본 구성 요소와 같은 일부 구성 요소에서는 외부 데이터에 연결해야 하며 이 용도로 패키지의 기존 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-135">Some components, such as the OLE DB Source component, require a connection to external data and use an existing <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object in the package for this purpose.</span></span> <span data-ttu-id="d1e29-136"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 속성은 구성 요소에 필요한 런타임 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체의 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection indicates the number of run-time <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects required by the component.</span></span> <span data-ttu-id="d1e29-137">이 수가 0보다 크면 해당 구성 요소에는 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-137">If the count is greater than zero, the component requires a connection.</span></span> <span data-ttu-id="d1e29-138"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A>에 있는 첫 번째 연결의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 속성을 지정하면 패키지의 연결 관리자를 구성 요소에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-138">Assign a connection manager from the package to the component by specifying the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> properties of the first connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span> <span data-ttu-id="d1e29-139">런타임 연결 컬렉션에 있는 연결 관리자의 이름은 패키지에서 참조하는 연결 관리자의 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-139">Note that the name of the connection manager in the run-time connection collection must match the name of the connection managerreferenced from the package.</span></span>  
  
## <a name="setting-the-values-of-custom-properties"></a><span data-ttu-id="d1e29-140">사용자 지정 속성 값 설정</span><span class="sxs-lookup"><span data-stu-id="d1e29-140">Setting the Values of Custom Properties</span></span>  
 <span data-ttu-id="d1e29-141">구성 요소의 디자인 타임 인스턴스를 만든 후에는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-141">After creating the design-time instance of the component, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="d1e29-142">이 메서드는 사용자 지정 속성과 입력 및 출력 개체를 만들어 새로 만든 구성 요소를 초기화하므로 생성자와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-142">This method is similar to a constructor because it initializes a newly created component by creating its custom properties and its input and output objects.</span></span> <span data-ttu-id="d1e29-143">한 구성 요소에 대해 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A>를 두 번 이상 호출하면 구성 요소가 다시 설정되고 이전의 메타데이터 수정 내용을 잃을 수 있으므로 이 메서드는 한 번만 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-143">Do not call <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> more than one time on a component, because the component may reset itself and lose any modifications previously made to its metadata.</span></span>  
  
 <span data-ttu-id="d1e29-144">구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A>에는 해당 구성 요소와 관련된 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 개체의 컬렉션이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-144">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> of the component contains a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> objects specific to the component.</span></span> <span data-ttu-id="d1e29-145">개체 속성을 해당 개체에서 항상 볼 수 있는 다른 프로그래밍 모델과 달리 구성 요소는 개발자가 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 메서드를 호출할 때 해당 구성 요소의 사용자 지정 속성 컬렉션만 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-145">Unlike other programming models, where the properties of an object are always visible on the object, components only populate their custom property collections when you call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="d1e29-146">메서드를 호출한 후에는 디자인 타임 구성 요소 인스턴스의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> 메서드를 사용하여 사용자 지정 속성에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-146">After you call method, use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> method of the design-time instance of the component to assign values to its custom properties.</span></span> <span data-ttu-id="d1e29-147">이 메서드는 사용자 지정 속성을 식별하고 새 값을 제공하는 이름/값 쌍을 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-147">This method accepts a name/value pair that identifies the custom property and provides its new value.</span></span>  
  
## <a name="initializing-output-columns"></a><span data-ttu-id="d1e29-148">출력 열 초기화</span><span class="sxs-lookup"><span data-stu-id="d1e29-148">Initializing Output Columns</span></span>  
 <span data-ttu-id="d1e29-149">구성 요소를 태스크에 추가하고 구성한 후에는 개체의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>에서 열 컬렉션을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-149">After you add a component to the task and configure it, initialize the collection of columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the object.</span></span> <span data-ttu-id="d1e29-150">이 단계는 특히 원본 구성 요소와 관련이 있지만 변환 및 대상 구성 요소는 일반적으로 업스트림 구성 요소에서 받는 열에 의존하므로 이러한 구성 요소의 열은 초기화하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-150">This step is especially relevant for source components, but may not initialize the columns for transformation and destination components because they generally depend on the columns that they receive from upstream components.</span></span>  
  
 <span data-ttu-id="d1e29-151">원본 구성 요소의 출력에 있는 열을 초기화하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-151">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> method to initialize the columns in the outputs of a source component.</span></span> <span data-ttu-id="d1e29-152">구성 요소에서는 외부 데이터 원본에 자동으로 연결하지 않으므로 구성 요소에서 외부 데이터 원본에 액세스하고 해당 열 메타데이터를 채울 수 있도록 하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A>를 호출하기 전에 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-152">Because components do not automatically connect to external data sources, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> method before calling <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> to provide the component access to its external data source and the ability to populate its column metadata.</span></span> <span data-ttu-id="d1e29-153">마지막으로 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> 메서드를 호출하여 연결을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-153">Finally, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> method to release the connection.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="d1e29-154">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d1e29-154">Next Step</span></span>  
 <span data-ttu-id="d1e29-155">구성 요소를 추가하고 구성한 다음에는 구성 요소 간의 경로를 만들어야 합니다. 이 단계에 대한 자세한 내용은 [프로그래밍 방식으로 데이터 흐름 구성 요소 연결](../building-packages-programmatically/connecting-data-flow-components-programmatically.md) 항목에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-155">After adding and configuring the component, the next step is to create paths between components, which is discussed in the topic, [Creating a Path Between Two Components](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="d1e29-156">샘플</span><span class="sxs-lookup"><span data-stu-id="d1e29-156">Sample</span></span>  
 <span data-ttu-id="d1e29-157">다음 코드 예제에서는 데이터 흐름 태스크에 OLE DB 원본 구성 요소를 추가하고 해당 구성 요소의 디자인 타임 인스턴스를 만든 다음 구성 요소의 속성을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-157">The following code sample adds the OLE DB Source component to a data flow task, creates a design-time instance of the component, and configures the component's properties.</span></span> <span data-ttu-id="d1e29-158">이 예에는 Microsoft.SqlServer.DTSRuntimeWrap 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d1e29-158">This example requires an additional reference to the assembly Microsoft.SqlServer.DTSRuntimeWrap.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Runtime.Package package = new Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Runtime.TaskHost thMainPipe = e as Runtime.TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Add an OLEDB connection manager to the package.  
      ConnectionManager cm = package.Connections.Add("OLEDB");  
      cm.Name = "OLEDB ConnectionManager";  
      cm.ConnectionString = "Data Source=(local);" +   
        "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" +   
        "Integrated Security=SSPI;"  
  
      // Add an OLE DB source to the data flow.  
      IDTSComponentMetaData100 component =   
        dataFlowTask.ComponentMetaDataCollection.New();  
      component.Name = "OLEDBSource";  
      component.ComponentClassID = "DTSAdapter.OleDbSource.1";  
      // You can also use the CLSID of the component instead of the PROGID.  
      //component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
      // Get the design time instance of the component.  
      CManagedComponentWrapper instance = component.Instantiate();  
  
      // Initialize the component  
      instance.ProvideComponentProperties();  
  
      // Specify the connection manager.  
      if (component.RuntimeConnectionCollection.Count > 0)  
      {  
        component.RuntimeConnectionCollection[0].ConnectionManager =   
          DtsConvert.GetExtendedInterface(package.Connections[0]);  
        component.RuntimeConnectionCollection[0].ConnectionManagerID =   
          package.Connections[0].ID;      }  
  
      // Set the custom properties.  
      instance.SetComponentProperty("AccessMode", 2);  
      instance.SetComponentProperty("SqlCommand",   
        "Select * from Production.Product");  
  
      // Reinitialize the metadata.  
      instance.AcquireConnections(null);  
      instance.ReinitializeMetaData();  
      instance.ReleaseConnections();  
  
      // Add other components to the data flow and connect them.  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Add an OLEDB connection manager to the package.  
    Dim cm As ConnectionManager = package.Connections.Add("OLEDB")  
    cm.Name = "OLEDB ConnectionManager"  
    cm.ConnectionString = "Data Source=(local);" & _  
      "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;"  
  
    ' Add an OLE DB source to the data flow.  
    Dim component As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component.Name = "OLEDBSource"  
    component.ComponentClassID = "DTSAdapter.OleDbSource.1"  
    ' You can also use the CLSID of the component instead of the PROGID.  
    'component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
    ' Get the design time instance of the component.  
    Dim instance As CManagedComponentWrapper = component.Instantiate()  
  
    ' Initialize the component.  
    instance.ProvideComponentProperties()  
  
    ' Specify the connection manager.  
    If component.RuntimeConnectionCollection.Count > 0 Then  
      component.RuntimeConnectionCollection(0).ConnectionManager = _  
        DtsConvert.GetExtendedInterface(package.Connections(0))  
      component.RuntimeConnectionCollection(0).ConnectionManagerID = _  
        package.Connections(0).ID  
    End If  
  
    ' Set the custom properties.  
    instance.SetComponentProperty("AccessMode", 2)  
    instance.SetComponentProperty("SqlCommand", _  
      "Select * from Production.Product")  
  
    ' Reinitialize the metadata.  
    instance.AcquireConnections(vbNull)  
    instance.ReinitializeMetaData()  
    instance.ReleaseConnections()  
  
    ' Add other components to the data flow and connect them.  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="d1e29-159">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="d1e29-159">External Resources</span></span>  
 <span data-ttu-id="d1e29-160">blogs.msdn.com의 블로그 항목 - [EzAPI – SQL Server 2012용으로 업데이트됨](https://go.microsoft.com/fwlink/?LinkId=243223)</span><span class="sxs-lookup"><span data-stu-id="d1e29-160">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="d1e29-161">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="d1e29-161">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d1e29-162">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e29-162">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d1e29-163">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e29-163">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d1e29-164">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="d1e29-164">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e29-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1e29-165">See Also</span></span>  
 [<span data-ttu-id="d1e29-166">프로그래밍 방식으로 데이터 흐름 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="d1e29-166">Connecting Data Flow Components Programmatically</span></span>](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
  
  
