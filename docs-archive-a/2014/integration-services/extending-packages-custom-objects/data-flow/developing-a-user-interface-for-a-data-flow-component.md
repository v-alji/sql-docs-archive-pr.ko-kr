---
title: 데이터 흐름 구성 요소의 사용자 인터페이스 개발 | Microsoft Docs
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
- data flow components [Integration Services], custom editors
- user interfaces [Integration Services]
- custom data flow components [Integration Services], custom editors
- custom component editors [Integration Services]
- IDtsComponentUI interface
- UITypeName property
- custom user interface [Integration Services], custom data flow component
- editors [Integration Services]
ms.assetid: 10b829a1-609b-42e3-9070-cfe5a2bb698c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f97f21ad14a5fa67fb49192931a0cb46d0cb41da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729664"
---
# <a name="developing-a-user-interface-for-a-data-flow-component"></a><span data-ttu-id="7530f-102">데이터 흐름 구성 요소의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="7530f-102">Developing a User Interface for a Data Flow Component</span></span>
  <span data-ttu-id="7530f-103">구성 요소 개발자는 구성 요소를 편집할 때 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에 표시되는 사용자 지정 사용자 인터페이스를 구성 요소에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-103">Component developers can provide a custom user interface for a component, which is displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] when the component is edited.</span></span> <span data-ttu-id="7530f-104">사용자 지정 사용자 인터페이스를 구현하면 해당 구성 요소가 데이터 흐름 태스크에 추가되거나 데이터 흐름 태스크에서 삭제될 때와 해당 구성 요소에 대한 도움말이 요청될 때 이에 대한 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-104">Implementing a custom user interface provides you with notification when the component is added to or deleted from a data flow task, and when help is requested for the component.</span></span>

 <span data-ttu-id="7530f-105">구성 요소에 사용자 지정 사용자 인터페이스를 제공하지 않는 경우에도 최종 사용자는 고급 편집기를 사용하여 구성 요소와 해당 구성 요소의 사용자 지정 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-105">If you do not provide a custom user interface for your component, users can still configure the component and its custom properties by using the Advanced Editor.</span></span> <span data-ttu-id="7530f-106">고급 편집기에서는 적절할 때 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 속성을 사용하여 사용자 지정 속성 값을 적절하게 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-106">You can ensure that the Advanced Editor allows users to edit custom property values appropriately by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> properties of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> when appropriate.</span></span> <span data-ttu-id="7530f-107">자세한 내용은 [데이터 흐름 구성 요소의 디자인 타임 메서드](design-time-methods-of-a-data-flow-component.md)의 "사용자 지정 속성 만들기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7530f-107">For more information, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>

## <a name="setting-the-uitypename-property"></a><span data-ttu-id="7530f-108">UITypeName 속성 설정</span><span class="sxs-lookup"><span data-stu-id="7530f-108">Setting the UITypeName Property</span></span>
 <span data-ttu-id="7530f-109">사용자 지정 사용자 인터페이스를 개발하려면 개발자는 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 속성을 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 인터페이스를 구현하는 클래스의 이름으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-109">To provide a custom user interface, the developer must set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> to the name of a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="7530f-110">구성 요소에서 이 속성이 설정된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서는 구성 요소가 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 편집될 때 사용자 지정 사용자 인터페이스를 로드하고 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-110">When this property is set by the component, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] loads and calls the custom user interface when the component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="7530f-111"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 속성은 해당 형식의 정규화된 이름을 식별하는 쉼표로 구분된 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property is a comma-delimited string that identifies the fully qualified name of the type.</span></span> <span data-ttu-id="7530f-112">다음 목록에서는 형식 식별 요소를 순서대로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-112">The following list shows, in order, the elements that identify the type:</span></span>

-   <span data-ttu-id="7530f-113">형식 이름</span><span class="sxs-lookup"><span data-stu-id="7530f-113">Type name</span></span>

-   <span data-ttu-id="7530f-114">어셈블리 이름</span><span class="sxs-lookup"><span data-stu-id="7530f-114">Assembly name</span></span>

-   <span data-ttu-id="7530f-115">파일 버전</span><span class="sxs-lookup"><span data-stu-id="7530f-115">File version</span></span>

-   <span data-ttu-id="7530f-116">문화권</span><span class="sxs-lookup"><span data-stu-id="7530f-116">Culture</span></span>

-   <span data-ttu-id="7530f-117">공개 키 토큰</span><span class="sxs-lookup"><span data-stu-id="7530f-117">Public key token</span></span>

 <span data-ttu-id="7530f-118">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 기본 클래스에서 파생되는 클래스를 보여 주고 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-118">The following code example shows a class that derives from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class and specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property.</span></span>

```csharp
[DtsPipelineComponent(
DisplayName="SampleComponent",
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...",
ComponentType = ComponentType.Transform)]
public class SampleComponent : PipelineComponent
{
//TODO: Implement the component here.
}
```

```vb
<DtsPipelineComponent(DisplayName="SampleComponent", _
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...", ComponentType=ComponentType.Transform)> _ 
Public Class SampleComponent 
 Inherits PipelineComponent 
End Class
```

## <a name="implementing-the-idtscomponentui-interface"></a><span data-ttu-id="7530f-119">IDtsComponentUI 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="7530f-119">Implementing the IDtsComponentUI Interface</span></span>
 <span data-ttu-id="7530f-120"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 인터페이스에는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 구성 요소가 추가, 삭제 및 편집될 때 호출하는 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-120">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface contains methods that [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls when a component is added, deleted, and edited.</span></span> <span data-ttu-id="7530f-121">구성 요소 개발자는 이러한 메서드의 구현에서 구성 요소 사용자와 상호 작용하기 위한 코드를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-121">Component developers can provide code in their implementation of these methods to interact with users of the component.</span></span>

 <span data-ttu-id="7530f-122">이 클래스는 일반적으로 구성 요소와는 별개의 어셈블리에 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-122">This class is typically implemented in an assembly separate from the component itself.</span></span> <span data-ttu-id="7530f-123">반드시 별개의 어셈블리를 사용해야 하는 것은 아니지만 이렇게 하면 개발자가 구성 요소와 사용자 인터페이스를 서로 독립적으로 빌드 및 배포하고 구성 요소의 이진 사용 공간을 작게 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-123">Although use of a separate assembly is not required, this lets the developer build and deploy the component and the user interface independently of each other, and keeps the binary footprint of the component small.</span></span>

 <span data-ttu-id="7530f-124">사용자 지정 사용자 인터페이스를 구현하면 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 해당 구성 요소가 편집될 때 구성 요소 개발자가 구성 요소를 보다 효율적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-124">Implementing a custom user interface gives the component developer more control over the component as it is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="7530f-125">예를 들어 구성 요소에서는 구성 요소가 처음 데이터 흐름 태스크에 추가될 때 호출되는 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> 메서드에 코드를 추가하고, 구성 요소의 초기 구성을 사용자에게 안내해 주는 마법사를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-125">For example, a component can add code to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> method, which is called when a component is initially added to a data flow task, and display a wizard that guides the user through the initial configuration of the component.</span></span>

 <span data-ttu-id="7530f-126"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 인터페이스를 구현하는 클래스를 만든 후에는 사용자와 구성 요소의 상호 작용에 응답하기 위한 코드를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-126">After you have created a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, you must add code to respond to user interaction with the component.</span></span> <span data-ttu-id="7530f-127"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 메서드는 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스를 제공하며, <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 메서드보다 먼저 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-127">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component, and is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> methods.</span></span> <span data-ttu-id="7530f-128">이 참조는 프라이빗 멤버 변수에 저장되어 이후 구성 요소의 메타데이터를 수정하는 데 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-128">This reference should be stored in a private member variable and used to modify the component's metadata thereafter.</span></span>

## <a name="modifying-a-component-and-persisting-changes"></a><span data-ttu-id="7530f-129">구성 요소 수정 및 변경 내용 지속</span><span class="sxs-lookup"><span data-stu-id="7530f-129">Modifying a Component and Persisting Changes</span></span>
 <span data-ttu-id="7530f-130"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스는 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 메서드에 대한 매개 변수로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-130">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface is provided as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method.</span></span> <span data-ttu-id="7530f-131">이 참조는 사용자 인터페이스에 의해 멤버 변수에 캐시된 다음 사용자와 사용자 인터페이스의 상호 작용에 대한 응답으로 구성 요소를 수정하는 데 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-131">This reference should be cached in a member variable by the user interface code, and then used to modify the component in response to user interaction with the user interface.</span></span>

 <span data-ttu-id="7530f-132"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스를 통해 직접 구성 요소를 수정할 수도 있지만 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 메서드를 사용하여 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A>의 인스턴스를 만드는 것이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-132">Although you can modify the component directly through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, it is better to create an instance of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method.</span></span> <span data-ttu-id="7530f-133">이 인터페이스를 사용하여 직접 구성 요소를 편집하면 구성 요소 보호를 위한 유효성 검사가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-133">When you edit the component directly by using the interface, you bypass the component's validation safeguards.</span></span> <span data-ttu-id="7530f-134">그러나 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper>를 통해 구성 요소의 디자인 타임 인스턴스를 사용하면 구성 요소에서 해당 구성 요소에 대한 변경을 제어할 수 있다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-134">The advantage of using the design-time instance of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> is that you ensure that the component has control over the changes made to it.</span></span>

 <span data-ttu-id="7530f-135"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 메서드의 반환 값은 구성 요소의 변경 내용이 지속되는지 삭제되는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-135">The return value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method determines whether changes made to a component are persisted or discarded.</span></span> <span data-ttu-id="7530f-136">이 메서드가 `false`를 반환하면 모든 변경 내용이 삭제되고, `true`를 반환하면 구성 요소의 변경 내용이 유지되고 패키지가 저장되어야 하는 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-136">When this method returns `false`, all changes are discarded; `true` persists the changes to the component and marks the package as needing to be saved.</span></span>

### <a name="using-the-services-of-the-ssis-designer"></a><span data-ttu-id="7530f-137">SSIS 디자이너의 서비스 사용</span><span class="sxs-lookup"><span data-stu-id="7530f-137">Using the Services of the SSIS Designer</span></span>
 <span data-ttu-id="7530f-138"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 메서드의 `IServiceProvider` 매개 변수는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너의 다음 서비스에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-138">The `IServiceProvider` parameter of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides access to the following services of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer:</span></span>

|<span data-ttu-id="7530f-139">서비스</span><span class="sxs-lookup"><span data-stu-id="7530f-139">Service</span></span>|<span data-ttu-id="7530f-140">Description</span><span class="sxs-lookup"><span data-stu-id="7530f-140">Description</span></span>|
|-------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsClipboardService>|<span data-ttu-id="7530f-141">구성 요소가 복사/붙여넣기 또는 잘라내기/붙여넣기 작업 중 어떤 작업의 일부로 생성되었는지를 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-141">Used to determine whether the component was generated as part of a copy/paste or cut/paste operation.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionService>|<span data-ttu-id="7530f-142">기존 연결에 액세스하거나 패키지에 새 연결을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-142">Used to access existing connections or to create new connections in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IErrorCollectionService>|<span data-ttu-id="7530f-143">마지막 오류 또는 경고만 받는 것이 아니라 구성 요소에 의해 발생한 오류 및 경고를 모두 캡처해야 하는 경우 데이터 흐름 구성 요소에서 발생한 이벤트를 캡처하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-143">Used to capture events from data flow components when you need to capture all the errors and warnings raised by the component instead of receiving only the last error or warning.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsVariableService>|<span data-ttu-id="7530f-144">기존 변수에 액세스하거나 패키지에 새 변수를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-144">Used to access existing variables or to create new variables in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsPipelineEnvironmentService>|<span data-ttu-id="7530f-145">데이터 흐름 구성 요소에서 부모 데이터 흐름 태스크와 데이터 흐름의 다른 구성 요소에 액세스하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-145">Used by data flow components to access the parent Data Flow task and other components in the data flow.</span></span> <span data-ttu-id="7530f-146">이 기능을 사용하면 필요할 때 추가 데이터 흐름 구성 요소를 만들고 연결하는 느린 변경 차원 마법사와 같은 구성 요소를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-146">This feature could be used to develop a component like the Slowly Changing Dimension Wizard that creates and connects additional data flow components as needed.</span></span>|

 <span data-ttu-id="7530f-147">개발자는 이러한 서비스를 사용하여 구성 요소가 로드된 패키지의 개체에 액세스하거나 패키지에 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-147">These services provide component developers the ability to access and create objects in the package in which the component is loaded.</span></span>

## <a name="sample"></a><span data-ttu-id="7530f-148">샘플</span><span class="sxs-lookup"><span data-stu-id="7530f-148">Sample</span></span>
 <span data-ttu-id="7530f-149">다음 코드 예제에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 인터페이스를 구현하는 사용자 지정 사용자 인터페이스 클래스와 구성 요소의 편집기로 사용되는 Windows Form의 통합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-149">The following code example shows the integration of a custom user interface class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, and a Windows form that serves as the editor for a component.</span></span>

### <a name="custom-user-interface-class"></a><span data-ttu-id="7530f-150">사용자 지정 사용자 인터페이스 클래스</span><span class="sxs-lookup"><span data-stu-id="7530f-150">Custom User Interface Class</span></span>
 <span data-ttu-id="7530f-151">다음 코드에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 인터페이스를 구현하는 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-151">The following code shows the class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="7530f-152"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 메서드는 구성 요소 편집기를 만든 다음 해당 폼을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-152">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method creates the component editor and then displays the form.</span></span> <span data-ttu-id="7530f-153">폼의 반환 값은 구성 요소의 변경 내용이 지속되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-153">The return value of the form determines whether changes to the component are persisted.</span></span>

```csharp
using System;
using System.Windows.Forms;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Pipeline.Design;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    public class SampleComponentUI : IDtsComponentUI
    {
        IDTSComponentMetaData100 md;
        IServiceProvider sp;

        public void Help(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void New(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void Delete(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Variables vars, Connections cons)
        {
            // Create and display the form for the user interface.
            SampleComponentUIForm componentEditor = new SampleComponentUIForm(cons, vars, md);

            DialogResult result  = componentEditor.ShowDialog(parentWindow);

            if (result == DialogResult.OK)
                return true;

            return false;
        }
        public void Initialize(IDTSComponentMetaData100 dtsComponentMetadata, IServiceProvider serviceProvider)
        {
            // Store the component metadata.
            this.md = dtsComponentMetadata;
        }
    }
}
```

```vb
Imports System 
Imports System.Windows.Forms 
Imports Microsoft.SqlServer.Dts.Runtime 
Imports Microsoft.SqlServer.Dts.Pipeline.Design 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Class SampleComponentUI 
 Implements IDtsComponentUI 
   Private md As IDTSComponentMetaData100 
   Private sp As IServiceProvider 

   Public Sub Help(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub New(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub Delete(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal vars As Variables, ByVal cons As Connections) As Boolean 
     ' Create and display the form for the user interface.
     Dim componentEditor As SampleComponentUIForm = New SampleComponentUIForm(cons, vars, md) 
     Dim result As DialogResult = componentEditor.ShowDialog(parentWindow) 
     If result = DialogResult.OK Then 
       Return True 
     End If 
     Return False 
   End Function 

   Public Sub Initialize(ByVal dtsComponentMetadata As IDTSComponentMetaData100, ByVal serviceProvider As IServiceProvider) 
     Me.md = dtsComponentMetadata 
   End Sub 
 End Class 

End Namespace
```

### <a name="custom-editor"></a><span data-ttu-id="7530f-154">사용자 지정 편집기</span><span class="sxs-lookup"><span data-stu-id="7530f-154">Custom Editor</span></span>
 <span data-ttu-id="7530f-155">다음 코드에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 메서드를 호출하는 동안 표시되는 Windows Form의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7530f-155">The following code shows the implementation of the Windows form that is shown during the call to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method.</span></span>

```csharp
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;

using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    public partial class SampleComponentUIForm : System.Windows.Forms.Form
    {
        private Connections connections;
        private Variables variables;
        private IDTSComponentMetaData100 metaData;
        private CManagedComponentWrapper designTimeInstance;
        private System.ComponentModel.IContainer components = null;

        public SampleComponentUIForm( Connections cons, Variables vars, IDTSComponentMetaData100 md)
        {
            variables = vars;
            connections = cons;
            metaData = md;
        }

        private void btnOk_Click(object sender, System.EventArgs e)
        {
            if (designTimeInstance == null)
                designTimeInstance = metaData.Instantiate();

            designTimeInstance.SetComponentProperty( "CustomProperty", txtCustomPropertyValue.Text);

            this.Close();
        }

        private void btnCancel_Click(object sender, System.EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System 
Imports System.Drawing 
Imports System.Collections 
Imports System.ComponentModel 
Imports System.Windows.Forms 
Imports System.Data 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Partial Class SampleComponentUIForm 
  Inherits System.Windows.Forms.Form 
   Private connections As Connections 
   Private variables As Variables 
   Private metaData As IDTSComponentMetaData100 
   Private designTimeInstance As CManagedComponentWrapper 
   Private components As System.ComponentModel.IContainer = Nothing 

   Public Sub New(ByVal cons As Connections, ByVal vars As Variables, ByVal md As IDTSComponentMetaData100) 
     variables = vars 
     connections = cons 
     metaData = md 
   End Sub 

   Private Sub btnOk_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     If designTimeInstance Is Nothing Then 
       designTimeInstance = metaData.Instantiate 
     End If 
     designTimeInstance.SetComponentProperty("CustomProperty", txtCustomPropertyValue.Text) 
     Me.Close 
   End Sub 

   Private Sub btnCancel_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     Me.Close 
   End Sub 
 End Class 

End Namespace
```

<span data-ttu-id="7530f-156">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="7530f-156">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7530f-157">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="7530f-157">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7530f-158">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="7530f-158">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7530f-159">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="7530f-159">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="7530f-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7530f-160">See Also</span></span>
 [<span data-ttu-id="7530f-161">사용자 지정 데이터 흐름 구성 요소 만들기</span><span class="sxs-lookup"><span data-stu-id="7530f-161">Creating a Custom Data Flow Component</span></span>](creating-a-custom-data-flow-component.md)


