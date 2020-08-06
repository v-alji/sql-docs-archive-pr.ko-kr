---
title: 스크립트 태스크 코딩 및 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f4383469368ac1fe3c70ff82f8c8bb2cf755838
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728495"
---
# <a name="coding-and-debugging-the-script-task"></a><span data-ttu-id="aab5d-102">스크립트 태스크 코딩 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="aab5d-102">Coding and Debugging the Script Task</span></span>
  <span data-ttu-id="aab5d-103">**스크립트 태스크 편집기**에서 스크립트 태스크를 구성한 후에 스크립트 태스크 개발 환경에서 사용자 지정 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-103">After configuring the Script task in the **Script Task Editor**, you write your custom code in the Script task development environment.</span></span>

## <a name="script-task-development-environment"></a><span data-ttu-id="aab5d-104">스크립트 태스크 개발 환경</span><span class="sxs-lookup"><span data-stu-id="aab5d-104">Script Task Development Environment</span></span>
 <span data-ttu-id="aab5d-105">스크립트 태스크는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications)를 스크립트 자체의 개발 환경으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-105">The Script task uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the development environment for the script itself.</span></span>

 <span data-ttu-id="aab5d-106">스크립트 코드는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-106">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="aab5d-107">**스크립트 태스크 편집기**에서 **ScriptLanguage** 속성을 설정하여 스크립트 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-107">You specify the script language by setting the **ScriptLanguage** property in the **Script Task Editor**.</span></span> <span data-ttu-id="aab5d-108">다른 프로그래밍 언어를 사용하고 싶으면 원하는 언어로 사용자 지정 어셈블리를 개발하고 스크립트 태스크의 코드에서 해당 기능을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-108">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script task.</span></span>

 <span data-ttu-id="aab5d-109">스크립트 태스크에서 작성하는 스크립트는 패키지 정의에 저장되며</span><span class="sxs-lookup"><span data-stu-id="aab5d-109">The script that you create in the Script task is stored in the package definition.</span></span> <span data-ttu-id="aab5d-110">별도의 스크립트 파일은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-110">There is no separate script file.</span></span> <span data-ttu-id="aab5d-111">따라서 스크립트 태스크를 사용해도 패키지 배포에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-111">Therefore, the use of the Script task does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="aab5d-112">패키지를 디자인하고 스크립트를 디버깅할 때 스크립트 코드는 임시로 프로젝트 파일에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-112">When you design the package and debug the script, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="aab5d-113">중요한 정보를 파일에 저장하면 보안상 위험할 수 있으므로 암호와 같은 중요한 정보는 스크립트 코드에 포함하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-113">Because storing sensitive information in a file is a potential security risk, we recommend that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="aab5d-114">기본적으로 `Option Strict`는 IDE에서 비활성화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-114">By default, `Option Strict` is disabled in the IDE.</span></span>

## <a name="script-task-project-structure"></a><span data-ttu-id="aab5d-115">스크립트 태스크 프로젝트 구조</span><span class="sxs-lookup"><span data-stu-id="aab5d-115">Script Task Project Structure</span></span>
 <span data-ttu-id="aab5d-116">스크립트 태스크에 포함되는 스크립트를 만들거나 수정할 경우 VSTA에서는 빈 새 프로젝트가 열리거나 기존 프로젝트가 다시 열립니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-116">When you create or modify the script that is contained in a Script task, VSTA opens an empty new project or reopens the existing project.</span></span> <span data-ttu-id="aab5d-117">이 프로젝트는 패키지 파일 내에 저장되며 스크립트 태스크에서는 추가 파일을 만들지 않으므로 이 VSTA 프로젝트를 만들어도 패키지의 배포에는 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-117">The creation of this VSTA project does not affect the deployment of the package, because the project is saved inside the package file; the Script task does not create additional files.</span></span>

### <a name="project-items-and-classes-in-the-script-task-project"></a><span data-ttu-id="aab5d-118">스크립트 태스크 프로젝트의 프로젝트 항목 및 클래스</span><span class="sxs-lookup"><span data-stu-id="aab5d-118">Project Items and Classes in the Script Task Project</span></span>
 <span data-ttu-id="aab5d-119">기본적으로 VSTA 프로젝트 탐색기 창에 표시되는 스크립트 태스크 프로젝트에는 `ScriptMain`이라는 단일 항목이 포함되어 있으며,</span><span class="sxs-lookup"><span data-stu-id="aab5d-119">By default, the Script task project displayed in the VSTA Project Explorer window contains a single item, `ScriptMain`.</span></span> <span data-ttu-id="aab5d-120">이 `ScriptMain` 항목에는 역시 `ScriptMain`이라는 단일 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-120">The `ScriptMain` item, in turn, contains a single class, also named `ScriptMain`.</span></span> <span data-ttu-id="aab5d-121">클래스의 코드 요소는 스크립트 태스크용으로 선택한 프로그래밍 언어에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-121">The code elements in the class vary depending on the programming language that you selected for the Script task:</span></span>

-   <span data-ttu-id="aab5d-122">스크립트 태스크가 프로그래밍 언어에 대해 구성 된 경우 [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] 클래스에는 `ScriptMain` 공용 서브루틴가 `Main` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-122">When the Script task is configured for the [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] programming language, the `ScriptMain` class has a public subroutine, `Main`.</span></span> <span data-ttu-id="aab5d-123">`ScriptMain.Main` 서브루틴은 개발자가 스크립트 태스크를 실행할 때 런타임에서 호출하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-123">The `ScriptMain.Main` subroutine is the method that the runtime calls when you run your Script task.</span></span>

     <span data-ttu-id="aab5d-124">기본적으로 새 스크립트의 `Main` 서브루틴에 있는 유일한 코드는 `Dts.TaskResult = ScriptResults.Success` 줄뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-124">By default, the only code in the `Main` subroutine of a new script is the line `Dts.TaskResult = ScriptResults.Success`.</span></span> <span data-ttu-id="aab5d-125">이 줄은 태스크가 작업에 성공했음을 런타임에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-125">This line informs the runtime that the task was successful in its operation.</span></span> <span data-ttu-id="aab5d-126">`Dts.TaskResult`속성은 [스크립트 태스크에서 결과 반환](../../extending-packages-scripting/task/returning-results-from-the-script-task.md)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-126">The `Dts.TaskResult` property is discussed in [Returning Results from the Script Task](../../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>

-   <span data-ttu-id="aab5d-127">스크립트 태스크가 Visual C# 프로그래밍 언어를 사용하도록 구성된 경우 `ScriptMain` 클래스에는 `Main`이라는 공용 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-127">When the Script task is configured for the Visual C# programming language, the `ScriptMain` class has a public method, `Main`.</span></span> <span data-ttu-id="aab5d-128">이 메서드는 스크립트 태스크가 실행될 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-128">The method is called when the Script task runs.</span></span>

     <span data-ttu-id="aab5d-129">기본적으로 `Main` 메서드에는 `Dts.TaskResult = (int)ScriptResults.Success` 줄이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-129">By default, the `Main` method includes the line `Dts.TaskResult = (int)ScriptResults.Success`.</span></span> <span data-ttu-id="aab5d-130">이 줄은 태스크가 작업에 성공했음을 런타임에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-130">This line informs the runtime that the task was successful in its operation.</span></span>

 <span data-ttu-id="aab5d-131">`ScriptMain` 항목에는 `ScriptMain` 이외의 클래스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-131">The `ScriptMain` item can contain classes other than the `ScriptMain` class.</span></span> <span data-ttu-id="aab5d-132">클래스는 해당 클래스가 있는 스크립트 태스크에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-132">Classes are available only to the Script task in which they reside.</span></span>

 <span data-ttu-id="aab5d-133">기본적으로 `ScriptMain` 프로젝트 항목에는 다음과 같은 자동 생성 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-133">By default, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="aab5d-134">코드 템플릿은 또한 스크립트 태스크에 대한 개요와 SSIS 개체(예: 변수, 이벤트 및 연결)를 검색 및 조작하는 방법에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-134">The code template also provides an overview of the Script task, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Task
' Write scripts using Microsoft Visual Basic 2008.
' The ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy

<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _
Partial Class ScriptMain

Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup

End Sub

Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown
Try
' Unlock variables from the read-only and read-write variable collection properties
If (Dts.Variables.Count <> 0) Then
Dts.Variables.Unlock()
End If
Catch ex As Exception
        End Try
End Sub

Enum ScriptResults
Success = DTSExecResult.Success
Failure = DTSExecResult.Failure
End Enum

' The execution engine calls this method when the task executes.
' To access the object model, use the Dts property. Connections, variables, events,
' and logging features are available as members of the Dts property as shown in the following examples.
'
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)
'
' To use the connections collection use something like the following:
' ConnectionManager cm = Dts.Connections.Add("OLEDB")
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"
'
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.
' 
' To open Help, press F1.

Public Sub Main()
'
' Add your code here
'
Dts.TaskResult = ScriptResults.Success
End Sub

End Class
```

```csharp
/*
   Microsoft SQL Server Integration Services Script Task
   Write scripts using Microsoft Visual C# 2008.
   The ScriptMain is the entry point class of the script.
*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;
using System.Windows.Forms;

namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj
{
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]
    public partial class ScriptMain
    {
        private void ScriptMain_Startup(object sender, EventArgs e)
        {

        }

        private void ScriptMain_Shutdown(object sender, EventArgs e)
        {
            try
            {
                // Unlock variables from the read-only and read-write variable collection properties
                if (Dts.Variables.Count != 0)
                {
                    Dts.Variables.Unlock();
                }
            }
            catch
            {
            }
        }

        #region VSTA generated code
        private void InternalStartup()
        {
            this.Startup += new System.EventHandler(ScriptMain_Startup);
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);
        }
        enum ScriptResults
        {
            Success = DTSExecResult.Success,
            Failure = DTSExecResult.Failure
        };

        #endregion

        /*
The execution engine calls this method when the task executes.
To access the object model, use the Dts property. Connections, variables, events,
and logging features are available as members of the Dts property as shown in the following examples.

To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;
To post a log entry, call Dts.Log("This is my log text", 999, null);
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);

To use the connections collection use something like the following:
ConnectionManager cm = Dts.Connections.Add("OLEDB");
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";

Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.

To open Help, press F1.
*/

        public void Main()
        {
            // TODO: Add your code here
            Dts.TaskResult = (int)ScriptResults.Success;
        }
    }
```

### <a name="additional-project-items-in-the-script-task-project"></a><span data-ttu-id="aab5d-135">스크립트 태스크 프로젝트의 추가 프로젝트 항목</span><span class="sxs-lookup"><span data-stu-id="aab5d-135">Additional Project Items in the Script Task Project</span></span>
 <span data-ttu-id="aab5d-136">스크립트 태스크 프로젝트는 기본 `ScriptMain` 항목 외에 다른 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-136">The Script task project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="aab5d-137">이 프로젝트에는 클래스, 모듈 및 코드 파일을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-137">You can add classes, modules, and code files to the project.</span></span> <span data-ttu-id="aab5d-138">폴더를 사용하여 항목 그룹을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-138">You can also use folders to organize groups of items.</span></span> <span data-ttu-id="aab5d-139">추가하는 모든 항목은 패키지 내부에 지속됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-139">All the items that you add are persisted inside the package.</span></span>

### <a name="references-in-the-script-task-project"></a><span data-ttu-id="aab5d-140">스크립트 태스크 프로젝트의 참조</span><span class="sxs-lookup"><span data-stu-id="aab5d-140">References in the Script Task Project</span></span>
 <span data-ttu-id="aab5d-141">**프로젝트 탐색기**에서 스크립트 태스크 프로젝트를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 클릭하여 관리되는 어셈블리에 대한 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-141">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="aab5d-142">자세한 내용은 [스크립팅 솔루션에서 다른 어셈블리 참조](../referencing-other-assemblies-in-scripting-solutions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aab5d-142">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="aab5d-143">프로젝트 참조는 VSTA IDE의 **클래스 뷰** 또는 **프로젝트 탐색기**에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-143">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="aab5d-144">**보기** 메뉴에서 이러한 창 중 하나를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-144">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="aab5d-145">**프로젝트** 메뉴, **프로젝트 탐색기** 또는 **클래스 뷰**에서 새 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-145">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-task"></a><span data-ttu-id="aab5d-146">스크립트 태스크에서 패키지와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="aab5d-146">Interacting with the Package in the Script Task</span></span>
 <span data-ttu-id="aab5d-147">스크립트 태스크에서는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 클래스의 인스턴스인 전역 `Dts` 개체와 해당 멤버를 사용하여 포함하는 패키지 및 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임과 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-147">The Script task uses the global `Dts` object, which is an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, and its members to interact with the containing package and with the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

 <span data-ttu-id="aab5d-148">다음 표에서는 전역 `Dts` 개체를 통해 스크립트 태스크 코드에 제공되는 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 클래스의 주요 공용 멤버를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-148">The following table lists the principal public members of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, which is exposed to Script task code through the global `Dts` object.</span></span> <span data-ttu-id="aab5d-149">이 섹션의 항목에서는 이러한 멤버의 사용 방법을 보다 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-149">The topics in this section discuss the use of these members in more detail.</span></span>

|<span data-ttu-id="aab5d-150">멤버</span><span class="sxs-lookup"><span data-stu-id="aab5d-150">Member</span></span>|<span data-ttu-id="aab5d-151">목적</span><span class="sxs-lookup"><span data-stu-id="aab5d-151">Purpose</span></span>|
|------------|-------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|<span data-ttu-id="aab5d-152">패키지에 정의된 연결 관리자에 액세스할 수 있게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-152">Provides access to connection managers defined in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|<span data-ttu-id="aab5d-153">스크립트 태스크에서 오류, 경고 및 정보 메시지를 발생시킬 수 있게 해 주는 이벤트 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-153">Provides an events interface to let the Script task raise errors, warnings, and informational messages.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|<span data-ttu-id="aab5d-154">`TaskResult` 외에도 간단한 방법으로 런타임에 단일 개체를 반환할 수 있게 해 줍니다. 반환된 단일 개체는 워크플로 분기에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-154">Provides a simple way to return a single object to the runtime (in addition to the `TaskResult`) that can also be used for workflow branching.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|<span data-ttu-id="aab5d-155">사용하도록 설정된 로그 공급자에 태스크 진행률 및 결과 등의 정보를 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-155">Logs information such as task progress and results to enabled log providers.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|<span data-ttu-id="aab5d-156">태스크의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-156">Reports the success or failure of the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|<span data-ttu-id="aab5d-157">태스크의 컨테이너가 실행 중인 트랜잭션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-157">Provides the transaction, if any, within which the task's container is running.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|<span data-ttu-id="aab5d-158">스크립트 내에서 사용하기 위해 `ReadOnlyVariables` 및 `ReadWriteVariables` 태스크 속성에 나열된 변수에 액세스할 수 있게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-158">Provides access to the variables listed in the `ReadOnlyVariables` and `ReadWriteVariables` task properties for use within the script.</span></span>|

 <span data-ttu-id="aab5d-159"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 클래스에는 대개 사용하지 않는 공용 멤버도 일부 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-159">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class also contains some public members that you will probably not use.</span></span>

|<span data-ttu-id="aab5d-160">멤버</span><span class="sxs-lookup"><span data-stu-id="aab5d-160">Member</span></span>|<span data-ttu-id="aab5d-161">Description</span><span class="sxs-lookup"><span data-stu-id="aab5d-161">Description</span></span>|
|------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|<span data-ttu-id="aab5d-162"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성은 변수에 보다 편리하게 액세스할 수 있게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-162">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property provides more convenient access to variables.</span></span> <span data-ttu-id="aab5d-163"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>를 사용할 수도 있지만 읽기 및 쓰기를 위해 변수를 잠그거나 잠금 해제하려면 명시적으로 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-163">Although you can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must explicitly call methods to lock and unlock variables for reading and writing.</span></span> <span data-ttu-id="aab5d-164">스크립트 태스크에서는 개발자가 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 사용할 때 잠금 의미 체계를 자동으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-164">The Script task handles locking semantics for you when you use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>|

## <a name="debugging-the-script-task"></a><span data-ttu-id="aab5d-165">스크립트 태스크 디버깅</span><span class="sxs-lookup"><span data-stu-id="aab5d-165">Debugging the Script Task</span></span>
 <span data-ttu-id="aab5d-166">스크립트 태스크의 코드를 디버깅하려면 코드에 하나 이상의 중단점을 설정한 다음 VSTA IDE를 닫고 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-166">To debug the code in your Script task, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="aab5d-167">패키지 실행 중 스크립트 태스크 실행이 시작되면 VSTA IDE가 다시 열리고 코드가 읽기 전용 모드에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-167">When package execution enters the Script task, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="aab5d-168">중단점에 도달한 후에는 변수 값을 검사하고 나머지 코드를 단계별로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-168">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!WARNING]
>  <span data-ttu-id="aab5d-169">64비트 모드로 패키지를 실행할 때 스크립트 태스크를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-169">You can debug the Script task when you run the package in 64-bit mode.</span></span>

> [!NOTE]
>  <span data-ttu-id="aab5d-170">스크립트 태스크를 디버깅하려면 패키지를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-170">You must execute the package to debug into your Script task.</span></span> <span data-ttu-id="aab5d-171">개별 태스크만 실행하면 스크립트 태스크 코드의 중단점이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-171">If you execute only the individual task, breakpoints in the Script task code are ignored.</span></span>

> [!NOTE]
>  <span data-ttu-id="aab5d-172">스크립트 태스크를 패키지 실행 태스크에서 실행된 자식 패키지의 일부로 실행할 경우에는 스크립트 태스크를 디버깅할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-172">You cannot debug a Script task when you run the Script task as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="aab5d-173">이러한 경우에는 자식 패키지에서 스크립트 태스크에 설정한 중단점이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-173">Breakpoints that you set in the Script task in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="aab5d-174">자식 패키지는 별도로 실행하여 정상적으로 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-174">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="aab5d-175">여러 스크립트 태스크가 포함되어 있는 패키지를 디버깅하는 경우 디버거는 한 개의 스크립트 태스크를 디버깅합니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-175">When you debug a package that contains multiple Script tasks, the debugger debugs one Script task.</span></span> <span data-ttu-id="aab5d-176">Foreach 루프 또는 For 루프 컨테이너의 경우와 같이 디버거가 완료되는 경우 시스템에서 다른 스크립트 태스크를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aab5d-176">The system can debug another Script task if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

## <a name="external-resources"></a><span data-ttu-id="aab5d-177">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="aab5d-177">External Resources</span></span>

-   <span data-ttu-id="aab5d-178">blogs.msdn.com의 블로그 항목 - [SSIS 2008 및 R2 설치의 VSTA 설치 및 구성 문제](https://go.microsoft.com/fwlink/?LinkId=215661)</span><span class="sxs-lookup"><span data-stu-id="aab5d-178">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="aab5d-179">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="aab5d-179">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="aab5d-180">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]의 최신 다운로드, 아티클, 예제 및 비디오와 커뮤니티의 정선된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하십시오.</span><span class="sxs-lookup"><span data-stu-id="aab5d-180">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="aab5d-181">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="aab5d-181">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="aab5d-182">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="aab5d-182">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="aab5d-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aab5d-183">See Also</span></span>
 <span data-ttu-id="aab5d-184">[스크립팅 솔루션에서 다른 어셈블리 참조](../referencing-other-assemblies-in-scripting-solutions.md) [스크립트 태스크 편집기에서 스크립트 태스크 구성](configuring-the-script-task-in-the-script-task-editor.md)</span><span class="sxs-lookup"><span data-stu-id="aab5d-184">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) [Configuring the Script Task in the Script Task Editor](configuring-the-script-task-in-the-script-task-editor.md)</span></span>


