---
title: 스크립트 구성 요소 코딩 및 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9363ad447ca3d0031289eafb1d8f616320fca5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652215"
---
# <a name="coding-and-debugging-the-script-component"></a><span data-ttu-id="5d143-102">스크립트 구성 요소 코딩 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="5d143-102">Coding and Debugging the Script Component</span></span>
  <span data-ttu-id="5d143-103">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 스크립트 구성 요소에는 메타데이터 디자인 모드와 코드 디자인 모드의 두 가지 모드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-103">In [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata design mode and code design mode.</span></span> <span data-ttu-id="5d143-104">**스크립트 변환 편집기**를 열면 구성 요소가 메타데이터 디자인 모드로 전환됩니다. 여기서는 메타데이터를 구성하고 구성 요소 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-104">When you open the **Script Transformation Editor**, the component enters metadata design mode, in which you configure metadata and set component properties.</span></span> <span data-ttu-id="5d143-105">메타데이터 디자인 모드에서 스크립트 구성 요소 속성을 설정하고 입/출력을 구성한 후에는 코드 디자인 모드로 전환하여 사용자 지정 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-105">After you have set the properties of the Script component and configured the input and outputs in metadata design mode, you can switch to code design mode to write your custom script.</span></span> <span data-ttu-id="5d143-106">메타데이터 디자인 모드 및 코드 디자인 모드에 대한 자세한 내용은 [스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성](configuring-the-script-component-in-the-script-component-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-106">For more information about metadata design mode and code design mode, see [Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md).</span></span>

## <a name="writing-the-script-in-code-design-mode"></a><span data-ttu-id="5d143-107">코드 디자인 모드에서 스크립트 작성</span><span class="sxs-lookup"><span data-stu-id="5d143-107">Writing the Script in Code Design Mode</span></span>

### <a name="script-component-development-environment"></a><span data-ttu-id="5d143-108">스크립트 구성 요소 개발 환경</span><span class="sxs-lookup"><span data-stu-id="5d143-108">Script Component Development Environment</span></span>
 <span data-ttu-id="5d143-109">스크립트를 작성하려면 **스크립트 변환 편집기**의 **스크립트** 페이지에서 **스크립트 편집**을 클릭하여 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications) IDE를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-109">To write your script, click **Edit Script** on the **Script** page of the **Script Transformation Editor** to open the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE.</span></span> <span data-ttu-id="5d143-110">VSTA IDE에는 색 구분 기능이 포함된 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 편집기, IntelliSense, 개체 브라우저 등 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET 환경의 모든 표준 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-110">The VSTA IDE includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span>

 <span data-ttu-id="5d143-111">스크립트 코드는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-111">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="5d143-112">**스크립트 변환 편집기**에서 **ScriptLanguage** 속성을 설정하여 스크립트 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-112">You specify the script language by setting the **ScriptLanguage** property in the **Script Transformation Editor**.</span></span> <span data-ttu-id="5d143-113">다른 프로그래밍 언어를 사용하고 싶으면 원하는 언어로 사용자 지정 어셈블리를 개발하고 스크립트 구성 요소의 코드에서 해당 기능을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-113">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script component.</span></span>

 <span data-ttu-id="5d143-114">스크립트 구성 요소에서 작성하는 스크립트는 패키지 정의에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-114">The script that you create in the Script component is stored in the package definition.</span></span> <span data-ttu-id="5d143-115">별도의 스크립트 파일은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-115">There is no separate script file.</span></span> <span data-ttu-id="5d143-116">따라서 스크립트 구성 요소를 사용해도 패키지 배포에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-116">Therefore, the use of the Script component does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="5d143-117">패키지를 디자인하는 동안 스크립트 코드는 임시로 프로젝트 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-117">While you design the package, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="5d143-118">중요한 정보를 파일에 저장하면 보안상 위험할 수 있으므로 암호와 같은 중요한 정보는 스크립트 코드에 포함하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-118">Because storing sensitive information in a file is a potential security risk, we recommended that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="5d143-119">기본적으로 `Option Strict`는 IDE에서 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-119">By default, `Option Strict` is disabled in the IDE.</span></span>

### <a name="script-component-project-structure"></a><span data-ttu-id="5d143-120">스크립트 구성 요소 프로젝트 구조</span><span class="sxs-lookup"><span data-stu-id="5d143-120">Script Component Project Structure</span></span>
 <span data-ttu-id="5d143-121">스크립트 구성 요소의 장점은, 개발자가 작성해야 할 코드 분량을 줄여주는 인프라 코드를 생성할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-121">The power of the Script component is that it can generate infrastructure code that reduces the amount of code that you must write.</span></span> <span data-ttu-id="5d143-122">이 기능은 입/출력 및 해당 열과 속성이 고정되어 있고 미리 알려져 있다는 사실을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-122">This feature relies on the fact that inputs and outputs and their columns and properties are fixed and known in advance.</span></span> <span data-ttu-id="5d143-123">따라서 그 이후에 구성 요소의 메타데이터 내용을 변경하면 작성한 코드가 무효화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-123">Therefore, any subsequent changes that you make to the component's metadata may invalidate the code that you have written.</span></span> <span data-ttu-id="5d143-124">그러면 패키지 실행 중 컴파일 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-124">This causes compilation errors during execution of the package.</span></span>

#### <a name="project-items-and-classes-in-the-script-component-project"></a><span data-ttu-id="5d143-125">스크립트 구성 요소 프로젝트의 프로젝트 항목 및 클래스</span><span class="sxs-lookup"><span data-stu-id="5d143-125">Project Items and Classes in the Script Component Project</span></span>
 <span data-ttu-id="5d143-126">코드 디자인 모드로 전환하면 VSTA IDE에서 `ScriptMain` 프로젝트 항목을 열어 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-126">When you switch to code design mode, the VSTA IDE opens and displays the `ScriptMain` project item.</span></span> <span data-ttu-id="5d143-127">`ScriptMain` 프로젝트 항목은 스크립트의 진입점으로 사용되어 코드 작성 위치를 나타내는 편집 가능한 `ScriptMain` 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-127">The `ScriptMain` project item contains the editable `ScriptMain` class, which serves as the entry point for the script and which is where you write your code.</span></span> <span data-ttu-id="5d143-128">클래스의 코드 요소는 스크립트 태스크용으로 선택한 프로그래밍 언어에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-128">The code elements in the class vary depending on the programming language that you selected for the Script task.</span></span>

 <span data-ttu-id="5d143-129">스크립트 프로젝트는 다음과 같은 두 가지 추가 자동 생성 읽기 전용 프로젝트 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-129">The script project contains two additional auto-generated read-only project items:</span></span>

-   <span data-ttu-id="5d143-130">`ComponentWrapper` 프로젝트 항목은 다음의 세 클래스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-130">The `ComponentWrapper` project item contains three classes:</span></span>

    -   <span data-ttu-id="5d143-131">`UserComponent` 클래스 - <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>에서 상속되며, 데이터를 처리하고 패키지와 상호 작용하는 데 사용할 메서드와 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-131">The `UserComponent` class, which inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> and contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="5d143-132">`ScriptMain` 클래스는 `UserComponent` 클래스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-132">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

    -   <span data-ttu-id="5d143-133">`Connections` 컬렉션 클래스 - 스크립트 변환 편집기의 연결 관리자 페이지에서 선택한 연결에 대한 참조를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-133">A `Connections` collection class that contains references to the connections selected on the Connection Manager page of the Script Transformation Editor.</span></span>

    -   <span data-ttu-id="5d143-134">`Variables` `ReadOnlyVariable` `ReadWriteVariables` **스크립트 변환 편집기**의 **스크립트** 페이지에서 및 속성에 입력 한 변수에 대 한 참조를 포함 하는 컬렉션 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-134">A `Variables` collection class that contains references to the variables entered in the `ReadOnlyVariable` and `ReadWriteVariables` properties on the **Script** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="5d143-135">`BufferWrapper`프로젝트 항목에는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> **스크립트 변환 편집기**의 **입/출력** 페이지에 구성 된 각 입력 및 출력에 대해에서 상속 되는 클래스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-135">The `BufferWrapper` project item contains a class that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output configured on the **Inputs and Outputs** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="5d143-136">각 클래스는 구성된 입/출력 열과 그 열이 포함된 데이터 흐름 버퍼에 해당하는 형식화된 접근자 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-136">Each of these classes contains typed accessor properties that correspond to the configured input and output columns, and the data flow buffers that contain the columns.</span></span>

 <span data-ttu-id="5d143-137">이러한 개체, 메서드 및 속성을 사용하는 방법에 대한 자세한 내용은 [스크립트 구성 요소 개체 모델 이해](understanding-the-script-component-object-model.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-137">For information about how to use these objects, methods, and properties, see [Understanding the Script Component Object Model](understanding-the-script-component-object-model.md).</span></span> <span data-ttu-id="5d143-138">특정 유형의 스크립트 구성 요소에서 이러한 클래스의 메서드와 속성을 사용하는 방법에 대한 자세한 내용은 [추가 스크립트 구성 요소 예제](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-138">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="5d143-139">예 항목에는 전체 코드 예제도 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-139">The example topics also contain complete code samples.</span></span>

 <span data-ttu-id="5d143-140">스크립트 구성 요소를 변환으로 구성하면 `ScriptMain` 프로젝트 항목에 다음 자동 생성 코드가 들어갑니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-140">When you configure the Script component as a transformation, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="5d143-141">코드 템플릿은 또한 스크립트 구성 요소에 대한 개요와 SSIS 개체(예: 변수, 이벤트 및 연결)를 검색 및 조작하는 방법에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-141">The code template also provides an overview of the Script component, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Component
' Write scripts using Microsoft Visual Basic 2008.
' ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _
<CLSCompliant(False)> _
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub PreExecute()
        MyBase.PreExecute()
        '
        ' Add your code here for preprocessing or remove if not needed
        '
    End Sub

    Public Overrides Sub PostExecute()
        MyBase.PostExecute()
        '
        ' Add your code here for postprocessing or remove if not needed
        ' You can set read/write variables here, for example:
        ' Me.Variables.MyIntVar = 100
        '
    End Sub

    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)
        '
        ' Add your code here
        '
    End Sub

End Class
```

```csharp
/* Microsoft SQL Server Integration Services user script component
*  Write scripts using Microsoft Visual C# 2008.
*  ScriptMain is the entry point class of the script.*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]
public class ScriptMain : UserComponent
{

    public override void PreExecute()
    {
        base.PreExecute();
        /*
          Add your code here for preprocessing or remove if not needed
        */
    }

    public override void PostExecute()
    {
        base.PostExecute();
        /*
          Add your code here for postprocessing or remove if not needed
          You can set read/write variables here, for example:
          Variables.MyIntVar = 100
        */
    }

    public override void Input0_ProcessInputRow(Input0Buffer Row)
    {
        /*
          Add your code here
        */
    }

}
```

#### <a name="additional-project-items-in-the-script-component-project"></a><span data-ttu-id="5d143-142">스크립트 구성 요소 프로젝트의 추가 프로젝트 항목</span><span class="sxs-lookup"><span data-stu-id="5d143-142">Additional Project Items in the Script Component Project</span></span>
 <span data-ttu-id="5d143-143">스크립트 구성 요소 프로젝트는 기본 `ScriptMain` 항목 외에 다른 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-143">The Script component project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="5d143-144">클래스, 모듈, 코드 파일 및 폴더를 프로젝트에 추가할 수 있고, 항목 그룹을 구성하기 위해 폴더를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-144">You can add classes, modules, code files, and folders to the project, and you can use folders to organize groups of items.</span></span>

 <span data-ttu-id="5d143-145">추가하는 모든 항목은 패키지 내부에 지속됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-145">All the items that you add are persisted inside the package.</span></span>

#### <a name="references-in-the-script-component-project"></a><span data-ttu-id="5d143-146">스크립트 구성 요소 프로젝트의 참조</span><span class="sxs-lookup"><span data-stu-id="5d143-146">References in the Script Component Project</span></span>
 <span data-ttu-id="5d143-147">**프로젝트 탐색기**에서 스크립트 태스크 프로젝트를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 클릭하여 관리되는 어셈블리에 대한 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-147">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="5d143-148">자세한 내용은 [스크립팅 솔루션에서 다른 어셈블리 참조](../referencing-other-assemblies-in-scripting-solutions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-148">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="5d143-149">프로젝트 참조는 VSTA IDE의 **클래스 뷰** 또는 **프로젝트 탐색기**에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-149">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="5d143-150">**보기** 메뉴에서 이러한 창 중 하나를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-150">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="5d143-151">**프로젝트** 메뉴, **프로젝트 탐색기** 또는 **클래스 뷰**에서 새 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-151">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-component"></a><span data-ttu-id="5d143-152">스크립트 구성 요소에서 패키지와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="5d143-152">Interacting with the Package in the Script Component</span></span>
 <span data-ttu-id="5d143-153">스크립트 구성 요소에서 작성하는 사용자 지정 스크립트는 자동 생성된 기본 클래스의 강력한 형식의 접근자를 통해 포함하는 패키지에서 변수 및 연결 관리자를 액세스하고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-153">The custom script that you write in the Script component can access and use variables and connection managers from the containing package through strongly-typed accessors in the auto-generated base classes.</span></span> <span data-ttu-id="5d143-154">그러나 변수 및 연결 관리자를 스크립트에서 사용할 수 있게 만들려면 코드 디자인 모드로 들어가기 전에 이들을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-154">However, you must configure both variables and connection managers before entering code-design mode if you want to make them available to your script.</span></span> <span data-ttu-id="5d143-155">또한 스크립트 구성 요소 코드에서 이벤트를 발생시키고 로깅을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-155">You can also raise events and perform logging from your Script component code.</span></span>

 <span data-ttu-id="5d143-156">스크립트 구성 요소 프로젝트의 자동 생성된 프로젝트 항목은 다음과 같은 개체, 메서드 및 속성을 사용하여 패키지와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-156">The autogenerated project items in the Script component project provide the following objects, methods, and properties for interacting with the package.</span></span>

|<span data-ttu-id="5d143-157">패키지 기능</span><span class="sxs-lookup"><span data-stu-id="5d143-157">Package Feature</span></span>|<span data-ttu-id="5d143-158">액세스 방법</span><span class="sxs-lookup"><span data-stu-id="5d143-158">Access Method</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="5d143-159">variables</span><span class="sxs-lookup"><span data-stu-id="5d143-159">Variables</span></span>|<span data-ttu-id="5d143-160">`Variables` 클래스의 `ComponentWrapper` 속성을 통해 표시되는, `Variables` 프로젝트 항목의 `ScriptMain` 컬렉션 클래스에 있는 명명된 접근자 및 형식화된 접근자 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-160">Use the named and typed accessor properties in the `Variables` collection class in the `ComponentWrapper` project item, exposed through the `Variables` property of the `ScriptMain` class.</span></span><br /><br /> <span data-ttu-id="5d143-161">`PreExecute` 메서드는 읽기 전용 변수만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-161">The `PreExecute` method can access only read-only variables.</span></span> <span data-ttu-id="5d143-162">`PostExecute` 메서드는 읽기 전용 변수와 읽기/쓰기 변수 모두에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-162">The `PostExecute` method can access both read-only and read/write variables.</span></span>|
|<span data-ttu-id="5d143-163">Connections</span><span class="sxs-lookup"><span data-stu-id="5d143-163">Connections</span></span>|<span data-ttu-id="5d143-164">`Connections` 클래스의 `ComponentWrapper` 속성을 통해 표시되는, `Connections` 프로젝트 항목의 `ScriptMain` 컬렉션 클래스에 있는 명명된 접근자 및 형식화된 접근자 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-164">Use the named and typed accessor properties in the `Connections` collection class in the `ComponentWrapper` project item, exposed through the `Connections` property of the `ScriptMain` class.</span></span>|
|<span data-ttu-id="5d143-165">이벤트</span><span class="sxs-lookup"><span data-stu-id="5d143-165">Events</span></span>|<span data-ttu-id="5d143-166"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>클래스의 속성과 `ScriptMain` 인터페이스의 \*\* \<X> Fire\*\* 메서드를 사용 하 여 이벤트를 발생 시킵니다 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> .</span><span class="sxs-lookup"><span data-stu-id="5d143-166">Raise events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class and the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span>|
|<span data-ttu-id="5d143-167">로깅</span><span class="sxs-lookup"><span data-stu-id="5d143-167">Logging</span></span>|<span data-ttu-id="5d143-168">`ScriptMain` 클래스의 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 메서드를 사용하여 로깅을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-168">Perform logging by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class.</span></span>|

## <a name="debugging-the-script-component"></a><span data-ttu-id="5d143-169">스크립트 구성 요소 디버깅</span><span class="sxs-lookup"><span data-stu-id="5d143-169">Debugging the Script Component</span></span>
 <span data-ttu-id="5d143-170">스크립트 구성 요소의 코드를 디버깅하려면 코드에 하나 이상의 중단점을 설정한 다음 VSTA IDE를 닫고 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-170">To debug the code in your Script component, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="5d143-171">패키지 실행 중 스크립트 구성 요소 실행이 시작되면 VSTA IDE가 다시 열리고 코드가 읽기 전용 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-171">When package execution enters the Script component, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="5d143-172">중단점에 도달한 후에는 변수 값을 검사하고 나머지 코드를 단계별로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-172">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!NOTE]
>  <span data-ttu-id="5d143-173">스크립트 구성 요소를 패키지 실행 태스크에서 실행된 자식 패키지의 일부로 실행할 경우에는 스크립트 구성 요소를 디버깅할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-173">You cannot debug a Script component when you run the Script component as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="5d143-174">이러한 경우에는 자식 패키지에서 스크립트 구성 요소에 설정한 중단점이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-174">Breakpoints that you set in the Script component in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="5d143-175">자식 패키지는 별도로 실행하여 정상적으로 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-175">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="5d143-176">여러 스크립트 구성 요소가 포함되어 있는 패키지를 디버깅하는 경우 디버거는 한 개의 스크립트 구성 요소를 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-176">When you debug a package that contains multiple Script components, the debugger debugs one Script component.</span></span> <span data-ttu-id="5d143-177">Foreach 루프 또는 For 루프 컨테이너의 경우와 같이 디버거가 완료되는 경우 시스템에서 다른 스크립트 구성 요소를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-177">The system can debug another Script component if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

 <span data-ttu-id="5d143-178">다음 방법을 사용하여 스크립트 구성 요소의 실행을 모니터링할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-178">You can also monitor the execution of the Script component by using the following methods:</span></span>

-   <span data-ttu-id="5d143-179">실행을 중단 하 고 `MessageBox.Show` **system.object** 네임 스페이스의 메서드를 사용 하 여 모달 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-179">Interrupt execution and display a modal message by using the `MessageBox.Show` method in the **System.Windows.Forms** namespace.</span></span> <span data-ttu-id="5d143-180">(이 코드는 디버깅 프로세스를 완료한 후 제거하십시오.)</span><span class="sxs-lookup"><span data-stu-id="5d143-180">(Remove this code after you complete the debugging process.)</span></span>

-   <span data-ttu-id="5d143-181">정보 메시지, 경고 및 오류에 대한 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-181">Raise events for informational messages, warnings, and errors.</span></span> <span data-ttu-id="5d143-182">FireInformation, FireWarning 및 FireError 메서드는 Visual Studio **출력** 창에 이벤트 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-182">The FireInformation, FireWarning, and FireError methods display the event description in the Visual Studio **Output** window.</span></span> <span data-ttu-id="5d143-183">그러나 FireProgress 메서드, Console.Write 메서드 및 Console.WriteLine 메서드는 **출력** 창에 어떠한 정보도 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-183">However, the FireProgress method, the Console.Write method, and Console.WriteLine method do not display any information in the **Output** window.</span></span> <span data-ttu-id="5d143-184">FireProgress 이벤트의 메시지는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너의 **진행률** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-184">Messages from the FireProgress event appear on the **Progress** tab of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="5d143-185">자세한 내용은 [스크립트 구성 요소에서 이벤트 발생](../../data-flow/transformations/script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-185">For more information, see [Raising Events in the Script Component](../../data-flow/transformations/script-component.md).</span></span>

-   <span data-ttu-id="5d143-186">이벤트 또는 사용자 정의 메시지를 활성화된 로깅 공급자에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-186">Log events or user-defined messages to enabled logging providers.</span></span> <span data-ttu-id="5d143-187">자세한 내용은 [스크립트 구성 요소의 로깅](logging-in-the-script-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-187">For more information, see [Logging in the Script Component](logging-in-the-script-component.md).</span></span>

 <span data-ttu-id="5d143-188">데이터를 대상에 저장하지 않고 원본 또는 변형으로 구성된 스크립트 구성 요소의 출력을 검사하려는 경우, [행 개수 변환](../../data-flow/transformations/row-count-transformation.md)을 사용하여 데이터 흐름을 중지하고 데이터 뷰어를 스크립트 구성 요소의 출력에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-188">If you just want to examine the output of a Script component configured as a source or as a transformation, without saving the data to a destination, you can stop the data flow with a [Row Count Transformation](../../data-flow/transformations/row-count-transformation.md) and attach a data viewer to the output of the Script component.</span></span> <span data-ttu-id="5d143-189">데이터 뷰어에 대한 자세한 내용은 [데이터 흐름 디버깅](../../troubleshooting/debugging-data-flow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-189">For information about data viewers, see [Debugging Data Flow](../../troubleshooting/debugging-data-flow.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5d143-190">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5d143-190">In This Section</span></span>
 <span data-ttu-id="5d143-191">스크립트 구성 요소 코딩에 대한 자세한 내용은 이 섹션의 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5d143-191">For more information about coding the Script component, see the following topics in this section.</span></span>

 <span data-ttu-id="5d143-192">[스크립트 구성 요소 개체 모델 이해](understanding-the-script-component-object-model.md) 스크립트 구성 요소에서 사용할 수 있는 개체, 메서드 및 속성을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-192">[Understanding the Script Component Object Model](understanding-the-script-component-object-model.md) Explains how to use the objects, methods, and properties available in the Script component.</span></span>

 <span data-ttu-id="5d143-193">[스크립팅 솔루션에서 다른 어셈블리 참조](../referencing-other-assemblies-in-scripting-solutions.md) 스크립트 구성 요소의 클래스 라이브러리에서 개체를 참조 하는 방법을 설명 합니다 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5d143-193">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) Explains how to reference objects from the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library in the Script component.</span></span>

 <span data-ttu-id="5d143-194">[스크립트 구성 요소에 대 한 오류 출력 시뮬레이션](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md) 스크립트 구성 요소에서 처리 하는 동안 오류를 발생 시키는 행의 오류 출력을 시뮬레이트하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d143-194">[Simulating an Error Output for the Script Component](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md) Explains how to simulate an error output for rows that raise errors during processing by the Script component.</span></span>

## <a name="external-resources"></a><span data-ttu-id="5d143-195">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="5d143-195">External Resources</span></span>

-   <span data-ttu-id="5d143-196">blogs.msdn.com의 블로그 항목 - [SSIS 2008 및 R2 설치의 VSTA 설치 및 구성 문제](https://go.microsoft.com/fwlink/?LinkId=215661)</span><span class="sxs-lookup"><span data-stu-id="5d143-196">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="5d143-197">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="5d143-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5d143-198">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5d143-199">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5d143-200">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="5d143-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d143-201">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d143-201">See Also</span></span>
 [<span data-ttu-id="5d143-202">스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="5d143-202">Configuring the Script Component in the Script Component Editor</span></span>](configuring-the-script-component-in-the-script-component-editor.md)


