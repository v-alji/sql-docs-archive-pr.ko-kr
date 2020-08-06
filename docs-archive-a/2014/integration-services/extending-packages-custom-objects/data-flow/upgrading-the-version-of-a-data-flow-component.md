---
title: 데이터 흐름 구성 요소의 버전 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f494793a20f1cdcd108553278b82a44daeea75ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661250"
---
# <a name="upgrading-the-version-of-a-data-flow-component"></a><span data-ttu-id="4fde1-102">데이터 흐름 구성 요소의 버전 업그레이드</span><span class="sxs-lookup"><span data-stu-id="4fde1-102">Upgrading the Version of a Data Flow Component</span></span>
  <span data-ttu-id="4fde1-103">이전 버전의 구성 요소를 사용하여 만든 패키지에는 더 이상 유효하지 않은 메타데이터가 들어 있을 수 있습니다. 예를 들어 최신 버전의 구성 요소에서 사용법이 수정된 사용자 지정 속성이 이러한 메타데이터에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-103">Packages that were created with an older version of your component may contain metadata that is no longer valid, such as custom properties whose usage has been modified in newer versions of the component.</span></span> <span data-ttu-id="4fde1-104"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 기본 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 메서드를 재정의하여 이전 패키지에 이미 저장된 메타데이터를 현재 구성 요소 속성에 맞게 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-104">You can override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class to update the metadata previously saved in older packages to reflect the current properties of your component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fde1-105">구성 요소의 속성이 변경되지 않은 경우에는 새 버전의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 맞게 사용자 지정 구성 요소를 다시 컴파일할 때 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> 속성 값을 변경하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-105">When you recompile a custom component for a new version of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], you do not have to change the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property if the component's properties have not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fde1-106">예제</span><span class="sxs-lookup"><span data-stu-id="4fde1-106">Example</span></span>  
 <span data-ttu-id="4fde1-107">다음 예제에는 가상의 데이터 흐름 구성 요소 버전 2.0에 대한 코드가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-107">The following sample contains code from version 2.0 of a fictitious data flow component.</span></span> <span data-ttu-id="4fde1-108">새 버전 번호는 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 속성에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-108">The new version number is defined in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="4fde1-109">이 구성 요소에는 임계값을 초과하는 숫자 값의 처리 방법을 정의하는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-109">The component has a property that defines how numeric values that exceed a threshold are to be handled.</span></span> <span data-ttu-id="4fde1-110">이 가상 구성 요소의 버전 1.0에서 이 속성은 이름이 `RaiseErrorOnInvalidValue`였으며 해당 값으로는 부울 값 true 또는 false를 받아들였습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-110">In version 1.0 of the fictitious component, this property was named `RaiseErrorOnInvalidValue` and accepted a Boolean value of true or false.</span></span> <span data-ttu-id="4fde1-111">하지만 버전 2.0에서는 속성 이름이 `InvalidValueHandling`으로 바뀌었으며 해당 값으로는 사용자 지정 열거형의 가능한 네 개 값 중 하나를 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-111">In version 2.0 of the fictitious component, the property has been renamed to `InvalidValueHandling` and accepts one of four possible values from a custom enumeration.</span></span>  
  
 <span data-ttu-id="4fde1-112">다음 예제의 재정의된 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 메서드는 다음 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-112">The overridden <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the following sample performs the following actions:</span></span>  
  
-   <span data-ttu-id="4fde1-113">구성 요소의 현재 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-113">Gets the current version of the component.</span></span>  
  
-   <span data-ttu-id="4fde1-114">이전 사용자 지정 속성의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-114">Gets the value of the old custom property.</span></span>  
  
-   <span data-ttu-id="4fde1-115">사용자 지정 속성 컬렉션에서 이전 속성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-115">Removes the old property from the custom property collection.</span></span>  
  
-   <span data-ttu-id="4fde1-116">가능한 경우 이전 속성 값에 따라 새 사용자 지정 속성의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-116">Sets the value of the new custom property based on the value of the old property, if possible.</span></span>  
  
-   <span data-ttu-id="4fde1-117">버전 메타데이터를 현재 구성 요소 버전으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-117">Sets the version metadata to the current version of the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fde1-118">데이터 흐름 엔진에서는 해당 엔진의 버전 번호를 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 메서드에 *pipelineVersion* 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-118">The data flow engine passes its own version number into the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the *pipelineVersion* parameter.</span></span> <span data-ttu-id="4fde1-119">이 매개 변수는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 버전 1.0에서는 유용하지 않지만 이후 버전에서는 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-119">This parameter is not useful in version 1.0 of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], but may become useful in subsequent versions.</span></span>  
  
 <span data-ttu-id="4fde1-120">예제 코드에서는 사용자 지정 속성의 이전 부울 값에 직접 매핑하는 두 개의 열거형 값만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-120">The sample code uses only the two enumeration values that map directly to the prior Boolean values for the custom property.</span></span> <span data-ttu-id="4fde1-121">하지만 고급 편집기에서 또는 프로그래밍 방식으로 구성 요소의 사용자 지정 사용자 인터페이스를 사용하여 사용 가능한 다른 열거형 값을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fde1-121">Users can select the other available enumeration values through the component's custom user interface, in the Advanced Editor, or programmatically.</span></span> <span data-ttu-id="4fde1-122">고급 편집기에서 사용자 지정 속성의 열거형 값을 표시하는 방법은 [데이터 흐름 구성 요소의 디자인 타임 메서드](design-time-methods-of-a-data-flow-component.md)의 "사용자 지정 속성 만들기"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4fde1-122">For information on displaying enumeration values for a custom property in the Advanced Editor, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```  
  
<span data-ttu-id="4fde1-123">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="4fde1-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4fde1-124">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4fde1-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4fde1-125">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="4fde1-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4fde1-126">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="4fde1-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
