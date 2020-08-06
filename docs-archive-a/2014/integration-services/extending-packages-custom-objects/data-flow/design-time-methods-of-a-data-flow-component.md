---
title: 데이터 흐름 구성 요소의 디자인 타임 메서드 | Microsoft Docs
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
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e33fc4eb5805318dac217d2c5cbaedfd4bca70fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652959"
---
# <a name="design-time-methods-of-a-data-flow-component"></a><span data-ttu-id="00151-102">데이터 흐름 구성 요소의 디자인 타임 메서드</span><span class="sxs-lookup"><span data-stu-id="00151-102">Design-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="00151-103">실행 전 데이터 흐름 태스크에서 증분 변경 작업이 수행될 때 해당 데이터 흐름 태스크는 디자인 타임 상태에 있다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-103">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="00151-104">변경 작업에는 구성 요소의 추가 또는 제거, 구성 요소를 연결하는 경로 개체의 추가 또는 제거, 구성 요소의 메타데이터 변경 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-104">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="00151-105">메타데이터가 변경되면 구성 요소에서는 변경 내용을 모니터링하고 그에 따라 반응할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-105">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="00151-106">예를 들어 변경에 대한 응답으로 구성 요소에서는 특정 변경 작업을 허용하지 않거나 추가 변경 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-106">For example, a component can disallow certain changes or make additional changes in response to a change.</span></span> <span data-ttu-id="00151-107">디자인 타임에 디자이너는 디자인 타임 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 인터페이스를 통해 구성 요소와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-107">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>

## <a name="design-time-implementation"></a><span data-ttu-id="00151-108">디자인 타임 구현</span><span class="sxs-lookup"><span data-stu-id="00151-108">Design-Time Implementation</span></span>
 <span data-ttu-id="00151-109">구성 요소의 디자인 타임 인터페이스는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 인터페이스에 의해 기술됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-109">The design-time interface of a component is described by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span> <span data-ttu-id="00151-110">이 인터페이스를 명시적으로 구현하지는 않지만 이 인터페이스에 정의된 메서드를 잘 알고 있으면 구성 요소의 디자인 타임 인스턴스에 해당하는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 기본 클래스의 메서드를 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-110">Although you do not explicitly implement this interface, a familiarity with the methods defined in this interface will help you understand which methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class correspond to the design-time instance of a component.</span></span>

 <span data-ttu-id="00151-111">구성 요소를 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에 로드하면 구성 요소의 디자인 타임 인스턴스가 인스턴스화되고 구성 요소를 편집할 때 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 인터페이스의 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-111">When a component is loaded in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], the design-time instance of the component is instantiated and the methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface are called as the component is edited.</span></span> <span data-ttu-id="00151-112">기본 클래스의 구현을 사용하여 구성 요소에서 필요한 메서드만 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-112">The implementation of the base class lets you override only those methods that your component requires.</span></span> <span data-ttu-id="00151-113">대부분의 경우 이러한 메서드를 재정의하여 구성 요소가 적절하지 않게 편집되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-113">In many cases, you may override these methods to prevent inappropriate edits to a component.</span></span> <span data-ttu-id="00151-114">예를 들어 사용자가 구성 요소에 출력을 추가할 수 없도록 하려면 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-114">For example, to prevent users from adding an output to a component, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> method.</span></span> <span data-ttu-id="00151-115">이 메서드를 재정의하지 않고 기본 클래스에 구현된 메서드를 호출하면 구성 요소에 출력이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-115">Otherwise, when the implementation of this method by the base class is called, it adds an output to the component.</span></span>

 <span data-ttu-id="00151-116">구성 요소의 목적 또는 기능에 관계없이 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 메서드를 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-116">Regardless of the purpose or functionality of your component, you should override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> methods.</span></span> <span data-ttu-id="00151-117"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>에 대한 자세한 내용은 [데이터 흐름 구성 요소의 유효성 검사](validating-a-data-flow-component.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00151-117">For more information about <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>, see [Validating a Data Flow Component](validating-a-data-flow-component.md).</span></span>

## <a name="providecomponentproperties-method"></a><span data-ttu-id="00151-118">ProvideComponentProperties 메서드</span><span class="sxs-lookup"><span data-stu-id="00151-118">ProvideComponentProperties Method</span></span>
 <span data-ttu-id="00151-119">구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 메서드에서 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-119">The initialization of a component occurs in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="00151-120">이 메서드는 클래스 생성자와 비슷하며 데이터 흐름 태스크에 구성 요소를 추가하면 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 이 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-120">This method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer when a component is added to the data flow task, and is similar to a class constructor.</span></span> <span data-ttu-id="00151-121">구성 요소 개발자는 이 메서드가 호출될 때 구성 요소의 입력, 출력 및 사용자 지정 속성을 만들고 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-121">Component developers should create and initialize their inputs, outputs, and custom properties during this method call.</span></span> <span data-ttu-id="00151-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 메서드가 생성자와 다른 점은 구성 요소의 디자인 타임 인스턴스나 런타임 인스턴스가 인스턴스화될 때마다 호출되지는 않는다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="00151-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method differs from a constructor because it is not called every time that the design-time instance or run-time instance of the component is instantiated.</span></span>

 <span data-ttu-id="00151-123">이 메서드의 기본 클래스 구현에서는 구성 요소에 입력 및 출력을 추가하고 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 속성에 입력의 ID를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-123">The base class implementation of the method adds an input and an output to the component and assigns the ID of the input to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property.</span></span> <span data-ttu-id="00151-124">그러나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 기본 클래스에 의해 추가된 입력 및 출력 개체에는 이름이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-124">However, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the input and output objects added by the base class are not named.</span></span> <span data-ttu-id="00151-125">패키지의 구성 요소에 Name 속성이 설정되지 않은 입력 또는 출력 개체가 있는 경우 해당 패키지는 성공적으로 로드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-125">Packages that contain a component with input or output objects whose Name property is not set will not successfully load.</span></span> <span data-ttu-id="00151-126">따라서 기본 구현을 사용할 때는 기본 입력 및 출력의 Name 속성에 값을 명시적으로 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-126">Therefore, when you use the base implementation, you must assign values explicitly to the Name property of the default input and output.</span></span>

```csharp
public override void ProvideComponentProperties()
{
    /// TODO: Reset the component.
    /// TODO: Add custom properties.
    /// TODO: Add input objects.
    /// TODO: Add output objects.
}
```

```vb
Public Overrides Sub ProvideComponentProperties()
    ' TODO: Reset the component.
    ' TODO: Add custom properties.
    ' TODO: Add input objects.
    ' TODO: Add output objects.
End Sub
```

### <a name="creating-custom-properties"></a><span data-ttu-id="00151-127">사용자 지정 속성 만들기</span><span class="sxs-lookup"><span data-stu-id="00151-127">Creating Custom Properties</span></span>
 <span data-ttu-id="00151-128">구성 요소 개발자는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 메서드가 호출될 때 구성 요소에 사용자 지정 속성(<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>)을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-128">The call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method is where component developers should add custom properties (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) to the component.</span></span> <span data-ttu-id="00151-129">사용자 지정 속성에는 데이터 형식 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-129">Custom properties do not have a data type property.</span></span> <span data-ttu-id="00151-130">사용자 지정 속성의 데이터 형식은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> 속성에 할당한 값의 데이터 형식에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="00151-130">The data type of a custom property is set by the data type of the value that you assign to its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> property.</span></span> <span data-ttu-id="00151-131">그러나 사용자 지정 속성에 초기 값을 할당한 후에는 데이터 형식이 다른 값을 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-131">However, after you have assigned an initial value to the custom property, you cannot assign a value with a different data type.</span></span>

> [!NOTE]
>  <span data-ttu-id="00151-132"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 인터페이스는 `Object` 유형의 속성 값을 제한적으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-132">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> interface has limited support for property values of type `Object`.</span></span> <span data-ttu-id="00151-133">사용자 지정 속성의 값으로는 문자열 또는 정수와 같은 단순 형식의 배열만 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-133">The only object that you can store as the value of a custom property is an array of simple types such as strings or integers.</span></span>

 <span data-ttu-id="00151-134"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> 속성을 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> 열거형의 `CPET_NOTIFY`로 설정하여 사용자 지정 속성이 속성 식을 지원하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-134">You can indicate that your custom property supports property expressions by setting the value of its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> property to `CPET_NOTIFY` from the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> enumeration, as shown in the following example.</span></span> <span data-ttu-id="00151-135">사용자가 입력한 속성 식을 처리하거나 유효성을 검사하기 위한 코드를 추가할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-135">You do not have to add any code to handle or to validate the property expression entered by the user.</span></span> <span data-ttu-id="00151-136">속성의 기본값을 설정하고 해당 값의 유효성을 검사한 다음 값을 정상적으로 읽고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-136">You can set a default value for the property, validate its value, and read and use its value normally.</span></span>

```csharp
IDTSCustomProperty100 myCustomProperty;
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;
```

```vb
Dim myCustomProperty As IDTSCustomProperty100
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY
```

 <span data-ttu-id="00151-137">다음 예제와 같이 속성을 사용 하 여 사용자가 열거형의 사용자 지정 속성 값을 선택 하도록 제한할 수 있습니다 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> .이 예제에서는 라는 공용 열거형을 정의 했다고 가정 합니다 `MyValidValues` .</span><span class="sxs-lookup"><span data-stu-id="00151-137">You can limit users to selecting a custom property value from an enumeration by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> property, as shown in the following example, which assumes that you have defined a public enumeration named `MyValidValues`.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the type with the custom property.
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;
// Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne;  
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the type with the custom property.
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName 
' Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne
```

 <span data-ttu-id="00151-138">자세한 내용은 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022)의 "일반화된 형식 변환" 및 "방법: 형식 변환기 구현"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00151-138">For more information, see "Generalized Type Conversion" and "Implementing a Type Converter" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

 <span data-ttu-id="00151-139">다음 예와 같이 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 속성을 사용하여 사용자 지정 속성의 값에 사용자 지정 편집기 대화 상자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00151-139">You can specify a custom editor dialog box for the value of your custom property by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property, as shown in the following example.</span></span> <span data-ttu-id="00151-140">요구 사항에 맞는 기존 UI 형식 편집기 클래스를 찾을 수 없는 경우 먼저 `System.Drawing.Design.UITypeEditor`에서 상속되는 사용자 지정 형식 편집기를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-140">First, you must create a custom type editor that inherits from `System.Drawing.Design.UITypeEditor`, if you cannot locate an existing UI type editor class that fits your needs.</span></span>

```csharp
public class MyCustomTypeEditor : UITypeEditor
{
...
}
```

```vb
Public Class MyCustomTypeEditor
  Inherits UITypeEditor 
  ...
End Class
```

 <span data-ttu-id="00151-141">그런 다음 이 클래스를 사용자 지정 속성의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 속성 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00151-141">Next, specify this class as the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property of your custom property.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the editor with the custom property.
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the editor with the custom property.
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName
```

 <span data-ttu-id="00151-142">자세한 내용은 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022)의 "방법: UI 형식 편집기 구현"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00151-142">For more information, see "Implementing a UI Type Editor" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

<span data-ttu-id="00151-143">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="00151-143">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="00151-144">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="00151-144">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="00151-145">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="00151-145">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="00151-146">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="00151-146">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="00151-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00151-147">See Also</span></span>
 [<span data-ttu-id="00151-148">데이터 흐름 구성 요소의 런타임 메서드</span><span class="sxs-lookup"><span data-stu-id="00151-148">Run-time Methods of a Data Flow Component</span></span>](run-time-methods-of-a-data-flow-component.md)


