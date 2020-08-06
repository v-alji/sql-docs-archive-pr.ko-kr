---
title: 사용자 지정 태스크의 사용자 인터페이스 개발 | Microsoft Docs
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
- custom user interfaces [Integration Services]
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- custom tasks [Integration Services], user interface
- custom user interface [Integration Services], custom tasks
- user interface [Integration Services]
- SSIS custom tasks, user interface
ms.assetid: 1e940cd1-c5f8-4527-b678-e89ba5dc398a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed96bbc302cba4c207e5ce7b2e4fb4b74fed4ee2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660058"
---
# <a name="developing-a-user-interface-for-a-custom-task"></a><span data-ttu-id="db58e-102">사용자 지정 태스크의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="db58e-102">Developing a User Interface for a Custom Task</span></span>
  <span data-ttu-id="db58e-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 개체 모델을 사용하면 사용자 지정 태스크 개발자가 태스크의 사용자 지정 사용자 인터페이스를 쉽게 만들 수 있으며 이러한 태스크는 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에 통합 및 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] object model provides custom task developers the ability to easily create a custom user interface for a task that can then be integrated and displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="db58e-104">사용자 인터페이스는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 사용자에게 유용한 정보를 제공하고 사용자 지정 태스크의 속성 및 설정을 올바르게 구성할 수 있도록 안내해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-104">The user interface can provide helpful information to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and guide users to correctly configure the properties and settings of the custom task.</span></span>  
  
 <span data-ttu-id="db58e-105">태스크의 사용자 지정 사용자 인터페이스를 개발할 때는 두 개의 중요한 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-105">Developing a custom user interface for a task involves using two important classes.</span></span> <span data-ttu-id="db58e-106">다음 표에서는 이러한 클래스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-106">The following table describes those classes.</span></span>  
  
|<span data-ttu-id="db58e-107">클래스</span><span class="sxs-lookup"><span data-stu-id="db58e-107">Class</span></span>|<span data-ttu-id="db58e-108">Description</span><span class="sxs-lookup"><span data-stu-id="db58e-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<span data-ttu-id="db58e-109">관리되는 태스크를 식별하고, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 개체를 표시하고 개체와 상호 작용하는 방식을 제어하기 위해 해당 속성을 통해 디자인 타임 정보를 제공하는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-109">An attribute that identifies a managed task, and supplies design-time information through its properties to control how [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer displays and interacts with the object.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|<span data-ttu-id="db58e-110">태스크에서 해당 태스크를 사용자 지정 사용자 인터페이스와 연결하는 데 사용되는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-110">An interface used by the task to associate the task with its custom user interface.</span></span>|  
  
 <span data-ttu-id="db58e-111">이 섹션에서는 사용자 지정 태스크의 사용자 인터페이스를 개발할 때 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성 및 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 인터페이스가 하는 역할을 설명하고, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너 내에서 태스크를 만들고, 통합, 배포 및 디버깅하는 방법에 대한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-111">This section describes the role of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface when you are developing a user interface for a custom task, and provides details about how to create, integrate, deploy, and debug the task within [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="db58e-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 태스크의 사용자 인터페이스에 대한 여러 진입점을 제공합니다. 즉, 사용자는 바로 가기 메뉴에서 **편집**을 선택하거나, 태스크를 두 번 클릭하거나, 속성 시트의 아래쪽에 있는 **편집기 표시** 링크를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-112">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer provides multiple entry points to the user interface for the task: the user can select **Edit** on the shortcut menu, double-click the task, or click the **Show Editor** link at the bottom of the property sheet.</span></span> <span data-ttu-id="db58e-113">사용자가 이러한 진입점 중 하나에 액세스하면 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 태스크의 사용자 인터페이스가 들어 있는 어셈블리를 찾아서 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-113">When the user accesses one of these entry points, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer locates and loads the assembly that contains the user interface for the task.</span></span> <span data-ttu-id="db58e-114">태스크의 사용자 인터페이스는 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 사용자에게 표시되는 속성 대화 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-114">The user interface for the task is responsible for creating the properties dialog box that is displayed to the user in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="db58e-115">태스크와 태스크의 해당 사용자 인터페이스는 별개의 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-115">A task and its user interface are separate entities.</span></span> <span data-ttu-id="db58e-116">따라서 지역화, 배포 및 유지 관리 작업을 줄이려면 태스크와 태스크의 사용자 인터페이스를 별개의 어셈블리에 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-116">They should be implemented in separate assemblies to reduce localization, deployment, and maintenance work.</span></span> <span data-ttu-id="db58e-117">태스크 DLL은 태스크에 코딩된 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성 값에 들어 있는 정보를 제외하고는 사용자 인터페이스에 대한 어떤 정보도 로드하거나 호출하지 않으며 일반적으로 이러한 정보를 포함하지도 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-117">The task DLL does not load, call, or generally contain any knowledge of its user interface, except for the information that is contained in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute values coded in the task.</span></span> <span data-ttu-id="db58e-118">태스크와 사용자 인터페이스는 이러한 방식으로만 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-118">This is the only way that a task and its user interface are associated.</span></span>  
  
## <a name="the-dtstask-attribute"></a><span data-ttu-id="db58e-119">DtsTask 특성</span><span class="sxs-lookup"><span data-stu-id="db58e-119">The DtsTask Attribute</span></span>  
 <span data-ttu-id="db58e-120"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성은 태스크 클래스 코드에 포함되어 태스크와 해당 사용자 인터페이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-120">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute is included in the task class code to associate a task with its user interface.</span></span> <span data-ttu-id="db58e-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 이 특성의 속성을 사용하여 디자이너에 태스크를 표시하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-121">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the properties of the attribute to determine how to display the task in the designer.</span></span> <span data-ttu-id="db58e-122">이러한 속성에는 표시할 이름과 해당되는 경우 아이콘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-122">These properties include the name to display and the icon, if any.</span></span>  
  
 <span data-ttu-id="db58e-123">다음 표에서는 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성의 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-123">The following table describes the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute.</span></span>  
  
|<span data-ttu-id="db58e-124">속성</span><span class="sxs-lookup"><span data-stu-id="db58e-124">Property</span></span>|<span data-ttu-id="db58e-125">Description</span><span class="sxs-lookup"><span data-stu-id="db58e-125">Description</span></span>|  
|--------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>|<span data-ttu-id="db58e-126">제어 흐름 도구 상자에 태스크 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-126">Displays the task name in the Control Flow toolbox.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>|<span data-ttu-id="db58e-127"><xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>에서 상속된 태스크 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-127">The task description (inherited from <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>).</span></span> <span data-ttu-id="db58e-128">이 속성은 도구 설명에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-128">This property is shown in ToolTips.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A>|<span data-ttu-id="db58e-129">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에 표시되는 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-129">The icon displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.RequiredProductLevel%2A>|<span data-ttu-id="db58e-130">사용되는 경우 이 속성은 <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> 열거형의 값 중 하나로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-130">If used, set it to one of the values in the <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> enumeration.</span></span> <span data-ttu-id="db58e-131">`RequiredProductLevel = DTSProductLevel.None`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-131">For example, `RequiredProductLevel = DTSProductLevel.None`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskContact%2A>|<span data-ttu-id="db58e-132">태스크에 기술 지원이 필요한 경우를 위해 연락처 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-132">Holds contact information for occasions when the task requires technical support.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskType%2A>|<span data-ttu-id="db58e-133">태스크에 유형을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-133">Assigns a type to the task.</span></span>|  
|<span data-ttu-id="db58e-134">Attribute.TypeId</span><span class="sxs-lookup"><span data-stu-id="db58e-134">Attribute.TypeId</span></span>|<span data-ttu-id="db58e-135">파생 클래스에서 구현된 경우 이 특성에 대한 고유 식별자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-135">When implemented in a derived class, gets a unique identifier for this Attribute.</span></span> <span data-ttu-id="db58e-136">자세한 내용은 .NET Framework 클래스 라이브러리의 `Attribute.TypeID` 속성을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="db58e-136">For more information, see `Attribute.TypeID` property in the .NET Framework Class Library.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A>|<span data-ttu-id="db58e-137">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 어셈블리를 로드하는 데 사용되는 어셈블리 유형 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-137">The type name of the assembly that is used by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to load the assembly.</span></span> <span data-ttu-id="db58e-138">이 속성은 태스크의 사용자 인터페이스 어셈블리를 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-138">This property is used to find the user interface assembly for the task.</span></span>|  
  
 <span data-ttu-id="db58e-139">다음 코드 예에서는 클래스 정의 위에 코딩된 경우의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-139">The following code example shows the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> as it would look, coded above the class definition.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
 <span data-ttu-id="db58e-140">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 어셈블리 이름, 유형 이름, 버전, culture 및 공개 키 토큰이 들어 있는 특성의 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 속성을 사용하여 GAC(전역 어셈블리 캐시)에서 어셈블리를 찾고, 디자이너에서 사용할 수 있도록 해당 어셈블리를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-140">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property of the attribute that includes the assembly name, type name, version, culture, and public key token, to locate the assembly in the Global Assembly Cache (GAC) and load it for use by the designer.</span></span>  
  
 <span data-ttu-id="db58e-141">어셈블리를 찾은 후 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 특성의 다른 속성을 사용하여 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에 태스크의 이름, 아이콘 및 설명과 같은 추가 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-141">After the assembly has been located, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the other properties in the attribute to display additional information about the task in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, such as the name, icon, and description of the task.</span></span>  
  
 <span data-ttu-id="db58e-142"><xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> 속성은 태스크가 사용자에게 표시되는 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-142">The <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> properties specify how the task is presented to the user.</span></span> <span data-ttu-id="db58e-143"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> 속성에는 사용자 인터페이스 어셈블리에 포함된 아이콘의 리소스 ID가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-143">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> property contains the resource ID of the icon embedded in the user interface assembly.</span></span> <span data-ttu-id="db58e-144">디자이너에서는 어셈블리에서 ID를 기준으로 아이콘 리소스를 로드하고, 태스크가 패키지에 추가될 때 도구 상자와 디자이너 화면의 태스크 이름 옆에 해당 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-144">The designer loads the icon resource by ID from the assembly, and displays it next to the task name in the toolbox and on the designer surface when the task is added to a package.</span></span> <span data-ttu-id="db58e-145">태스크에서 아이콘 리소스를 제공하지 않는 경우에는 태스크의 기본 아이콘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-145">If a task does not provide an icon resource, the designer uses a default icon for the task.</span></span>  
  
## <a name="the-idtstaskui-interface"></a><span data-ttu-id="db58e-146">IDTSTaskUI 인터페이스</span><span class="sxs-lookup"><span data-stu-id="db58e-146">The IDTSTaskUI Interface</span></span>  
 <span data-ttu-id="db58e-147"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 인터페이스는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 태스크와 연결된 사용자 인터페이스를 초기화하고 표시하기 위해 호출하는 메서드 및 속성의 컬렉션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-147">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface defines the collection of methods and properties called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to initialize and display the user interface associated with the task.</span></span> <span data-ttu-id="db58e-148">태스크의 사용자 인터페이스가 호출되면 디자이너에서는 태스크 사용자 인터페이스를 작성할 때 해당 사용자 인터페이스에 의해 구현된 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> 메서드를 호출한 다음 태스크와 패키지의 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 컬렉션을 각각 매개 변수로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-148">When the user interface for a task is invoked, the designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> method, implemented by the task user interface when you wrote it, and then provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collections of the task and package, respectively, as parameters.</span></span> <span data-ttu-id="db58e-149">이러한 컬렉션은 로컬로 저장되었다가 나중에 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 메서드에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-149">These collections are stored locally, and used subsequently in the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method.</span></span>  
  
 <span data-ttu-id="db58e-150">디자이너에서는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 메서드를 호출하여 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에 표시되는 창을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-150">The designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method to request the window that is displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="db58e-151">태스크에서는 해당 태스크의 사용자 인터페이스가 들어 있는 창의 인스턴스를 만들고 표시를 위해 해당 사용자 인터페이스를 디자이너에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-151">The task creates an instance of the window that contains the user interface for the task, and returns the user interface to the designer for display.</span></span> <span data-ttu-id="db58e-152">일반적으로 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 개체는 오버로드된 생성자를 통해 창에 제공되므로 이들 개체를 사용하여 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-152">Typically, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> objects are provided to the window through an overloaded constructor so they can be used to configure the task.</span></span>  
  
 <span data-ttu-id="db58e-153">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 태스크 UI의 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 메서드를 호출하여 태스크의 사용자 인터페이스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-153">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method of the task UI to display the user interface for the task.</span></span> <span data-ttu-id="db58e-154">태스크 사용자 인터페이스는 이 메서드에서 Windows Form을 반환하고 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 이 폼을 모달 대화 상자로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-154">The task user interface returns the Windows form from this method, and [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer shows this form as a modal dialog box.</span></span> <span data-ttu-id="db58e-155">폼이 닫히면 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 폼의 `DialogResult` 속성 값을 검사하여 태스크가 수정되었는지와 수정 내용을 저장해야 하는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-155">When the form is closed, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer examines the value of the `DialogResult` property of the form to determine whether the task has been modified and if these modifications should be saved.</span></span> <span data-ttu-id="db58e-156">`DialogResult` 속성 값이 `OK`인 경우 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 태스크의 지속성 메서드를 호출하여 변경 내용을 저장하고, 그렇지 않은 경우 변경 내용은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-156">If the value of the `DialogResult` property is `OK`, the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the persistence methods of the task to save the changes; otherwise, the changes are discarded.</span></span>  
  
 <span data-ttu-id="db58e-157">다음 코드 예제에서는 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 인터페이스를 구현하며 SampleTaskForm이라는 Windows Form 클래스가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="db58e-157">The following code sample implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface, and assumes the existence of a Windows form class named SampleTaskForm.</span></span>  
  
```csharp  
using System;  
using System.Windows.Forms;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Design;  
  
namespace Sample  
{  
   public class HelloWorldTaskUI : IDtsTaskUI  
   {  
      TaskHost   taskHost;  
      Connections connections;  
      public void Initialize(TaskHost taskHost, IServiceProvider serviceProvider)  
      {  
         this.taskHost = taskHost;  
         IDtsConnectionService cs = serviceProvider.GetService  
         ( typeof( IDtsConnectionService ) ) as   IDtsConnectionService;   
         this.connections = cs.GetConnections();  
      }  
      public ContainerControl GetView()  
      {  
        return new HelloWorldTaskForm(this.taskHost, this.connections);  
      }  
     public void Delete(IWin32Window parentWindow)  
     {  
     }  
     public void New(IWin32Window parentWindow)  
     {  
     }  
   }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Design  
Imports System.Windows.Forms  
  
Public Class HelloWorldTaskUI  
  Implements IDtsTaskUI  
  
  Dim taskHost As TaskHost  
  Dim connections As Connections  
  
  Public Sub Initialize(ByVal taskHost As TaskHost, ByVal serviceProvider As IServiceProvider) _  
    Implements IDtsTaskUI.Initialize  
  
    Dim cs As IDtsConnectionService  
  
    Me.taskHost = taskHost  
    cs = DirectCast(serviceProvider.GetService(GetType(IDtsConnectionService)), IDtsConnectionService)  
    Me.connections = cs.GetConnections()  
  
  End Sub  
  
  Public Function GetView() As ContainerControl _  
    Implements IDtsTaskUI.GetView  
  
    Return New HelloWorldTaskForm(Me.taskHost, Me.connections)  
  
  End Function  
  
  Public Sub Delete(ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.Delete  
  
  End Sub  
  
  Public Sub [New](ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.[New]  
  
  End Sub  
  
End Class  
```  
  
<span data-ttu-id="db58e-158">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="db58e-158">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="db58e-159">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="db58e-159">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="db58e-160">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="db58e-160">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="db58e-161">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="db58e-161">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db58e-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db58e-162">See Also</span></span>  
 <span data-ttu-id="db58e-163">[사용자 지정 태스크 만들기](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="db58e-163">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="db58e-164">[사용자 지정 태스크 코딩](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="db58e-164">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="db58e-165">사용자 지정 태스크의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="db58e-165">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
