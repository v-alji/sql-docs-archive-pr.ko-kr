---
title: 데이터 흐름 구성 요소 유효성 검사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ReinitializeMetaData method
- Validate method
- component validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- data flow components [Integration Services], validating
- validation [Integration Services]
ms.assetid: 1a7d5925-b387-4e31-af7f-c7f3c5151040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9a78588c1e75697235e62e8955b65da466a37ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649117"
---
# <a name="validating-a-data-flow-component"></a><span data-ttu-id="01265-102">데이터 흐름 구성 요소의 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="01265-102">Validating a Data Flow Component</span></span>
  <span data-ttu-id="01265-103"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드는 올바르게 구성되지 않은 구성 요소가 실행되는 것을 방지하기 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="01265-103">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is provided to prevent execution of a component that is not configured correctly.</span></span> <span data-ttu-id="01265-104">이 메서드를 사용하여 구성 요소에 입력 및 출력 개체 수가 필요한 만큼 있는지, 구성 요소의 사용자 지정 속성 값이 허용되는 값인지, 필요한 경우 연결이 지정되어 있는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01265-104">Use this method to verify that a component has the expected number of input and output objects, that the custom properties of the component have acceptable values, and that any connections, if required, are specified.</span></span> <span data-ttu-id="01265-105">또한 이 메서드를 사용하여 입력 및 출력 컬렉션의 열 데이터 형식이 올바른지와 각 열의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>이 해당 구성 요소에 적절하게 설정되어 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01265-105">Use this method also to verify that the columns in the input and output collections have the correct data types and that the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType> of each column is set appropriately for the component.</span></span> <span data-ttu-id="01265-106">기본 클래스 구현은 유효성 검사 프로세스에서 구성 요소의 입력 열 컬렉션을 검사하고 컬렉션의 각 열이 업스트림 구성 요소의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100>에 있는 열을 참조하는지 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-106">The base class implementation assists in the validation process by checking the input column collection of the component and ensuring that each column in the collection refers to a column in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100> of the upstream component.</span></span>  
  
## <a name="validate-method"></a><span data-ttu-id="01265-107">Validate 메서드</span><span class="sxs-lookup"><span data-stu-id="01265-107">Validate Method</span></span>  
 <span data-ttu-id="01265-108"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 메서드는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 구성 요소를 편집할 때 반복적으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="01265-108">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method is called repeatedly when a component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="01265-109"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> 열거형의 반환 값을 통해 또는 경고 및 오류를 게시하여 구성 요소의 디자이너와 사용자에게 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01265-109">You can provide feedback to the designer and to users of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> enumeration return value, and by posting warnings and errors.</span></span> <span data-ttu-id="01265-110"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> 열거형에는 다양한 오류 단계를 나타내는 세 개의 값과 구성 요소가 올바르게 구성되어 있고 실행할 수 있는 상태인지를 나타내는 네 번째 값 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID>가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01265-110">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> enumeration contains three values that indicate various stages of failure, and a fourth, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID>, that indicates whether the component is correctly configured and ready to execute.</span></span>  
  
 <span data-ttu-id="01265-111"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> 값은 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>에 오류가 있는지와 해당 구성 요소에서 오류를 복구할 수 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01265-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> value indicates that an error exists in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>, and that the component can repair the errors.</span></span> <span data-ttu-id="01265-112">구성 요소에서 복구할 수 없는 메타데이터 오류가 발생하는 경우에는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 메서드에서 오류를 수정하면 안 되며 유효성 검사 도중 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>를 수정해서도 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01265-112">If a component encounters a metadata error that it can repair, it should not fix the error in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> should not be modified during validation.</span></span> <span data-ttu-id="01265-113">대신 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 메서드에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA>만 반환해야 하고, 구성 요소에서는 이 섹션의 뒷부분에 설명된 대로 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 메서드가 호출될 때 오류를 복구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-113">Instead, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method should return only <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA>, and the component should repair the error in a call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method, as described later in this section.</span></span>  
  
 <span data-ttu-id="01265-114"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> 값은 디자이너에서 구성 요소를 편집하는 방법으로는 해결할 수 없는 오류가 구성 요소에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01265-114">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> value indicates that the component has an error that can be rectified by editing the component in the designer.</span></span> <span data-ttu-id="01265-115">이 오류는 일반적으로 사용자 지정 속성 또는 필요한 연결이 지정되지 않았거나 올바르게 설정되지 않은 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-115">The error is typically caused by a custom property or a required connection that is not specified or is set incorrectly.</span></span>  
  
 <span data-ttu-id="01265-116">최종 오류 값은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT>입니다. 이 값은 패키지 XML을 편집하거나 개체 모델을 사용하여 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 속성을 직접 수정한 경우에만 발생하는 오류를 구성 요소에서 발견했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01265-116">The final error value is <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT>, which indicates that the component has discovered errors that should only occur if the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property has been modified directly, either by editing the package XML or by using the object model.</span></span> <span data-ttu-id="01265-117">이러한 종류의 오류는 예를 들어 구성 요소에서 입력을 하나만 추가했는데 유효성 검사 과정에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>에 둘 이상의 입력이 있음을 발견한 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-117">For example, this kind of error occurs when a component has added only a single input, but validation discovers that more than one input exists in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>.</span></span> <span data-ttu-id="01265-118">이 반환 값을 생성하는 오류는 **고급 편집기** 대화 상자에서 **다시 설정** 단추를 사용하여 구성 요소를 다시 설정하는 방법으로만 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01265-118">Errors that generate this return value can only be repaired by resetting the component by using the **Reset** button in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="01265-119">구성 요소에서는 오류 값을 반환할 뿐 아니라 유효성 검사 도중 경고 또는 오류를 게시하여 피드백을 제공하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-119">Besides returning error values, components provide feedback by posting warnings or errors during validation.</span></span> <span data-ttu-id="01265-120">이 메커니즘은 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 메서드에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-120">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods provide this mechanism.</span></span> <span data-ttu-id="01265-121">이러한 메서드가 호출되면 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 **오류 목록** 창에 해당 이벤트가 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="01265-121">When these methods are called, these events are posted in the **Error List** window of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="01265-122">그런 다음 구성 요소 개발자는 발생한 오류와 적절한 경우 이를 수정하는 방법에 대한 직접적인 피드백을 사용자에게 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01265-122">Component developers can then provide direct feedback to users on the errors that have occurred, and if appropriate, how to correct them.</span></span>  
  
 <span data-ttu-id="01265-123">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>의 재정의된 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01265-123">The following code example shows an overridden implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    bool pbCancel = false;  
  
    // Validate that there is one input.  
    if (ComponentMetaData.InputCollection.Count != 1)  
    {  
    ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, out pbCancel);  
    return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Validate that the UserName custom property is set.  
    if (ComponentMetaData.CustomPropertyCollection["UserName"].Value == null || ((string)ComponentMetaData.CustomPropertyCollection["UserName"].Value).Length == 0)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISBROKEN;  
    }  
  
    // Validate that there is one output.  
    if (ComponentMetaData.OutputCollection.Count != 1)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Let the base class verify that the input column reflects the output   
    // of the upstream component.  
    return base.Validate();  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
  
 Dim pbCancel As Boolean = False  
  
 ' Validate that there is one input.  
 If Not (ComponentMetaData.InputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Validate that the UserName custom property is set.  
 If ComponentMetaData.CustomPropertyCollection("UserName").Value Is Nothing OrElse CType(ComponentMetaData.CustomPropertyCollection("UserName").Value, String).Length = 0 Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISBROKEN   
 End If   
  
 ' Validate that there is one output.  
 If Not (ComponentMetaData.OutputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Let the base class verify that the input column reflects the output   
 ' of the upstream component.  
  
 Return MyBase.Validate   
  
End Function  
```  
  
## <a name="reinitializemetadata-method"></a><span data-ttu-id="01265-124">ReinitializeMetaData 메서드</span><span class="sxs-lookup"><span data-stu-id="01265-124">ReinitializeMetaData Method</span></span>  
 <span data-ttu-id="01265-125"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 메서드는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> 메서드에서 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>를 반환하는 구성 요소를 편집할 때마다 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="01265-125">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer whenever you edit a component that returns <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> from its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method.</span></span> <span data-ttu-id="01265-126">구성 요소에는 유효성 검사 도중 구성 요소에 의해 식별된 문제를 검색하고 수정하는 코드가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01265-126">Components should contain code that detects and corrects the problems identified by the component during validation.</span></span>  
  
 <span data-ttu-id="01265-127">다음 예에서는 유효성 검사 도중 문제를 검색하고 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 메서드에서 이러한 오류를 수정하는 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01265-127">The following example shows a component that detects problems during validation and fixes these errors in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method.</span></span>  
  
```csharp  
private bool areInputColumnsValid = true;  
public override DTSValidationStatus Validate()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
    bool Cancel = false;  
    foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
    {  
        try  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
        }  
        catch  
        {  
            ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, out Cancel);  
            areInputColumnsValid = false;  
            return DTSValidationStatus.VS_NEEDSNEWMETADATA;  
        }  
    }  
  
    return DTSValidationStatus.VS_ISVALID;  
}  
public override void ReinitializeMetaData()  
{  
    if (!areInputColumnsValid)  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection[0];  
        IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
        foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
  
            if (vColumn == null)  
                input.InputColumnCollection.RemoveObjectByID(column.ID);  
        }  
        areInputColumnsValid = true;  
    }  
}  
```  
  
```vb  
Private areInputColumnsValid As Boolean = True   
  
Public  Overrides Function Validate() As DTSValidationStatus   
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
 Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
 Dim Cancel As Boolean = False   
 For Each column As IDTSInputColumn100 In input.InputColumnCollection   
   Try   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
   Catch   
     ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, Cancel)   
     areInputColumnsValid = False   
     Return DTSValidationStatus.VS_NEEDSNEWMETADATA   
   End Try   
 Next   
 Return DTSValidationStatus.VS_ISVALID   
End Function   
  
Public  Overrides Sub ReinitializeMetaData()   
 If Not areInputColumnsValid Then   
   Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
   Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
   For Each column As IDTSInputColumn100 In input.InputColumnCollection   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
     If vColumn Is Nothing Then   
       input.InputColumnCollection.RemoveObjectByID(column.ID)   
     End If   
   Next   
   areInputColumnsValid = True   
 End If   
End Sub  
```  
  
<span data-ttu-id="01265-128">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="01265-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="01265-129">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="01265-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="01265-130">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="01265-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="01265-131">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="01265-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
