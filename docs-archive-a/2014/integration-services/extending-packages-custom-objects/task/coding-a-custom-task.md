---
title: 사용자 지정 태스크 코딩 | Microsoft Docs
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
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c369f4a7e8352be7ddde9e2e3938b47b0bcc1349
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652221"
---
# <a name="coding-a-custom-task"></a><span data-ttu-id="65748-102">사용자 지정 태스크 코딩</span><span class="sxs-lookup"><span data-stu-id="65748-102">Coding a Custom Task</span></span>
  <span data-ttu-id="65748-103">[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 기본 클래스에서 상속하는 클래스를 만들고 이 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성을 적용한 후에는 기본 클래스의 속성 및 메서드 구현을 재정의하여 사용자 지정 기능을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-103">After you have created a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>

## <a name="configuring-the-task"></a><span data-ttu-id="65748-104">태스크 구성</span><span class="sxs-lookup"><span data-stu-id="65748-104">Configuring the Task</span></span>

### <a name="validating-the-task"></a><span data-ttu-id="65748-105">태스크 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="65748-105">Validating the Task</span></span>
 <span data-ttu-id="65748-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지를 디자인하는 경우 모든 오류를 런타임에만 찾는 것이 아니라 태스크에 대한 설정 작업이 수행되는 즉시 올바르지 않거나 적절하지 않은 설정을 catch할 수 있도록 유효성 검사를 통해 각 태스크에 대한 설정을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-106">When you are designing an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package, you can use validation to verify settings on each task, so that you can catch incorrect or inappropriate settings as soon as they are set, instead of finding all errors at run-time only.</span></span> <span data-ttu-id="65748-107">유효성 검사의 목적은 태스크가 성공적으로 실행되지 못하게 하는 잘못된 설정이나 연결이 태스크에 포함되어 있는지 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="65748-107">The purpose of validation is to determine whether the task contains invalid settings or connections that will prevent it from running successfully.</span></span> <span data-ttu-id="65748-108">이렇게 하면 첫 번째 실행에서 실행될 가능성이 높은 태스크가 패키지에 포함되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-108">This makes sure that the package contains tasks that have a good chance of running on their first run.</span></span>

 <span data-ttu-id="65748-109">사용자 지정 코드에서 `Validate` 메서드를 사용하여 유효성 검사 기능을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-109">You can implement validation by using the `Validate` method in custom code.</span></span> <span data-ttu-id="65748-110">런타임 엔진에서는 태스크에 대해 `Validate` 메서드를 호출하여 해당 태스크의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-110">The run-time engine validates a task by calling the `Validate` method on the task.</span></span> <span data-ttu-id="65748-111">태스크 유효성 검사의 성공 여부를 결정하는 조건을 정의하고 평가 결과를 런타임 엔진에 알리는 작업은 태스크 개발자가 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-111">It is the responsibility of the task developer to define the criteria that give you a successful or failed task validation, and to notify the run-time engine of the result of this evaluation.</span></span>

#### <a name="task-abstract-base-class"></a><span data-ttu-id="65748-112">태스크 추상 기본 클래스</span><span class="sxs-lookup"><span data-stu-id="65748-112">Task Abstract Base Class</span></span>
 <span data-ttu-id="65748-113">[Microsoft.](/dotnet/api/microsoft.sqlserver.dts.runtime.task) s a s e. c a s. s a s. s a c. `Validate`</span><span class="sxs-lookup"><span data-stu-id="65748-113">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) abstract base class provides the `Validate` method that each task overrides to define its validation criteria.</span></span> <span data-ttu-id="65748-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 패키지를 디자인하는 동안 `Validate` 메서드를 자동으로 여러 번 호출하고 경고나 오류가 발생할 때 태스크의 구성과 관련된 문제를 식별하는 데 유용한 시각적 표시를 사용자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-114">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically calls the `Validate` method multiple times during package design, and provides visual cues to the user when warnings or errors occur to help identify problems with the configuration of the task.</span></span> <span data-ttu-id="65748-115">태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 열거형의 값을 반환하고 경고 및 오류 이벤트를 발생시켜 유효성 검사 결과를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-115">Tasks provide validation results by returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and by raising warning and error events.</span></span> <span data-ttu-id="65748-116">이러한 이벤트에는 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서 사용자에게 표시되는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-116">These events contain information that is displayed to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="65748-117">다음은 유효성 검사의 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="65748-117">Some examples for validation follow:</span></span>

-   <span data-ttu-id="65748-118">연결 관리자가 특정 파일 이름의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-118">A connection manager validates the specific file name.</span></span>

-   <span data-ttu-id="65748-119">연결 관리자가 입력 형식이 XML 파일과 같은 필요한 형식인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-119">A connection manager validates that the type of input is the expected type, such as an XML file.</span></span>

-   <span data-ttu-id="65748-120">데이터베이스 입력이 필요한 태스크에서 데이터베이스 연결이 아닌 연결을 통해 데이터를 받을 수 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-120">A task that expects database input verifies that it cannot receive data from a non-database connection.</span></span>

-   <span data-ttu-id="65748-121">태스크에서 해당 태스크에 설정된 다른 속성과 충돌하는 속성이 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-121">A task guarantees that none of its properties contradicts other properties set on the same task.</span></span>

-   <span data-ttu-id="65748-122">태스크에서 실행 시 태스크에 사용되는 필수 리소스를 모두 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-122">A task guarantees that all required resources used by the task at execution time are available.</span></span>

 <span data-ttu-id="65748-123">유효성 검사를 수행할 대상 항목을 결정할 때는 성능을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-123">Performance is something to consider in determining what is validated and what is not.</span></span> <span data-ttu-id="65748-124">예를 들어 태스크에 대한 입력이 대역폭이 낮거나 트래픽이 많은 네트워크 연결을 통해 이루어지는 경우</span><span class="sxs-lookup"><span data-stu-id="65748-124">For example, the input to a task might be a connection over a network that has low bandwidth or heavy traffic.</span></span> <span data-ttu-id="65748-125">유효성 검사를 통해 리소스의 사용 가능성을 확인하는 데는 몇 초 정도만 소요되지만</span><span class="sxs-lookup"><span data-stu-id="65748-125">The validation may take several seconds to process if you decide to validate that the resource is available.</span></span> <span data-ttu-id="65748-126">다른 유효성 검사 작업에는 사용량이 많은 서버로의 왕복이 필요하므로 유효성 검사 루틴의 속도가 느릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-126">Another validation may cause a round-trip to a server that is in high demand, and the validation routine might be slow.</span></span> <span data-ttu-id="65748-127">유효성을 검사할 수 있는 속성 및 설정은 여러 가지가 있지만 모든 속성 및 설정에 대해 유효성을 검사해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="65748-127">Although there are many properties and settings that can be validated, not everything should be validated.</span></span>

-   <span data-ttu-id="65748-128">태스크가 실행되기 전에 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서도 `Validate` 메서드의 코드를 호출하며 이때 유효성 검사가 실패하면 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서는 실행을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-128">The code in the `Validate` method is also called by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> before the task is run, and the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> cancels execution if validation fails.</span></span>

#### <a name="user-interface-considerations-during-validation"></a><span data-ttu-id="65748-129">유효성 검사 중 사용자 인터페이스 고려 사항</span><span class="sxs-lookup"><span data-stu-id="65748-129">User Interface Considerations during Validation</span></span>
 <span data-ttu-id="65748-130">이 경우 [에는](/dotnet/api/microsoft.sqlserver.dts.runtime.task) <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 메서드에 대 한 매개 변수로 인터페이스를 포함 합니다. `Validate`</span><span class="sxs-lookup"><span data-stu-id="65748-130">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) includes an <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface as a parameter to the `Validate` method.</span></span> <span data-ttu-id="65748-131"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 인터페이스에는 태스크에서 런타임 엔진에 이벤트를 발생시키기 위해 호출하는 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-131">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the methods that are called by the task in order to raise events to the run-time engine.</span></span> <span data-ttu-id="65748-132"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 메서드는 유효성 검사 중 경고 또는 오류 조건이 발생할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-132">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods are called when a warning or error condition occurs during validation.</span></span> <span data-ttu-id="65748-133">두 경고 메서드에는 동일한 매개 변수가 필요하며 이러한 매개 변수에는 오류 코드, 원본 구성 요소, 설명, 도움말 파일, 및 도움말 컨텍스트 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-133">Both warning methods require the same parameters, which include an error code, source component, description, Help file, and Help context information.</span></span> <span data-ttu-id="65748-134">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너에서는 이 정보를 사용하여 디자인 화면에 시각적 표시를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-134">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses this information to display visual cues on the design surface.</span></span> <span data-ttu-id="65748-135">디자이너에서 제공하는 시각적 표시로는 디자이너 화면에서 태스크 옆에 나타나는 느낌표 아이콘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-135">The visual cues that are provided by the designer include an exclamation icon that appears next to the task on the designer surface.</span></span> <span data-ttu-id="65748-136">이 시각적 표시는 실행을 계속하기 전에 태스크에 추가 구성이 필요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65748-136">This visual cue signals to the user that the task requires additional configuration before execution can continue.</span></span>

 <span data-ttu-id="65748-137">느낌표 아이콘에는 오류 메시지가 포함된 도구 설명도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-137">The exclamation icon also displays a ToolTip that contains an error message.</span></span> <span data-ttu-id="65748-138">오류 메시지는 태스크에서 이벤트의 설명 매개 변수로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-138">The error message is provided by the task in the description parameter of the event.</span></span> <span data-ttu-id="65748-139">오류 메시지는 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 **태스크 목록** 창에도 표시되어 사용자에게 모든 유효성 검사 오류를 볼 수 있는 중앙 위치를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-139">Error messages are also displayed in the **Task List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], providing the user with a central location for viewing all validation errors.</span></span>

#### <a name="validation-example"></a><span data-ttu-id="65748-140">유효성 검사 예</span><span class="sxs-lookup"><span data-stu-id="65748-140">Validation Example</span></span>
 <span data-ttu-id="65748-141">다음 코드 예에서는 `UserName` 속성을 사용하는 태스크를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65748-141">The following code example shows a task with a `UserName` property.</span></span> <span data-ttu-id="65748-142">이 속성은 유효성 검사를 성공적으로 수행하기 위한 필수 항목으로 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-142">This property has been specified as required for validation to succeed.</span></span> <span data-ttu-id="65748-143">이 속성이 설정되어 있지 않으면 태스크에서는 오류를 게시하고 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> 열거형의 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-143">If the property is not set, the task posts an error, and returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span> <span data-ttu-id="65748-144">`Validate` 메서드는 try/catch 블록에 래핑되며 예외가 발생하면 유효성 검사가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-144">The `Validate` method is wrapped in a try/catch block, and fails validation if an exception occurs.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string userName = "";

  public override DTSExecResult Validate(Connections connections,
     VariableDispenser variableDispenser, IDTSComponentEvents events,
     IDTSLogging log)
  {
    try
    {
      if (this.userName == "")
      {
        //   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);
        //   Fail validation.
        return DTSExecResult.Failure;
      }
      //   Return success.
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string UserName
  {
    get
    {
      return this.userName;
    }
    set
    {
      this.userName = value;
    }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _userName As String = ""

  Public Overrides Function Validate(ByVal connections As Connections, _
     ByVal variableDispenser As VariableDispenser, _
     ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging) As DTSExecResult

    Try
      If Me._userName = "" Then
        '   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)
        '   Fail validation.
        Return DTSExecResult.Failure
      End If
      '   Return success.
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property UserName() As String
    Get
      Return Me._userName
    End Get
    Set(ByVal Value As String)
      Me._userName = Value
    End Set
  End Property

End Class
```

### <a name="persisting-the-task"></a><span data-ttu-id="65748-145">태스크 지속</span><span class="sxs-lookup"><span data-stu-id="65748-145">Persisting the Task</span></span>
 <span data-ttu-id="65748-146">일반적으로 태스크의 사용자 지정 지속성은 구현할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-146">Ordinarily you do not have to implement custom persistence for a task.</span></span> <span data-ttu-id="65748-147">사용자 지정 지속성은 개체의 속성이 복합 데이터 형식을 사용할 때만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-147">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="65748-148">자세한 내용은[Integration Services 사용자 지정 개체 개발](../developing-custom-objects-for-integration-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="65748-148">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>

## <a name="executing-the-task"></a><span data-ttu-id="65748-149">태스크 실행</span><span class="sxs-lookup"><span data-stu-id="65748-149">Executing the Task</span></span>
 <span data-ttu-id="65748-150">이 섹션에서는 태스크에서 상속하고 재정의한 `Execute` 메서드의 사용 방법을 보여 주며,</span><span class="sxs-lookup"><span data-stu-id="65748-150">This section describes how to use the `Execute` method that is inherited and overridden by tasks.</span></span> <span data-ttu-id="65748-151">태스크 실행 결과에 대한 정보를 제공하는 다양한 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-151">This section also explains various ways of providing information about the results of task execution.</span></span>

### <a name="execute-method"></a><span data-ttu-id="65748-152">Execute 메서드</span><span class="sxs-lookup"><span data-stu-id="65748-152">Execute Method</span></span>
 <span data-ttu-id="65748-153">패키지에 포함된 태스크는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 런타임에서 해당 `Execute` 메서드를 호출하면 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-153">Tasks that are contained in a package run when the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls their `Execute` method.</span></span> <span data-ttu-id="65748-154">태스크는이 메서드에서 핵심 비즈니스 논리 및 기능을 구현 하 고, 메시지를 게시 하 고, 열거형에서 값을 반환 하 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 고, 속성의 속성을 재정의 하 여 실행 결과를 제공 합니다 `get` `ExecutionValue` .</span><span class="sxs-lookup"><span data-stu-id="65748-154">Tasks implement their core business logic and functionality in this method, and provide the results of execution by posting messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and overriding the property `get` of the `ExecutionValue` property.</span></span>

 <span data-ttu-id="65748-155">[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 기본 클래스는 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드의 기본 구현을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-155">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class provides a default implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="65748-156">사용자 지정 태스크에서는 이 메서드를 재정의하여 해당 태스크의 런타임 기능을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-156">The custom tasks override this method to define their run-time functionality.</span></span> <span data-ttu-id="65748-157"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 개체는 태스크를 런타임 엔진과 패키지의 다른 개체에서 격리하여 해당 태스크를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-157">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object wraps the task, isolating it from the run-time engine and the other objects in the package.</span></span> <span data-ttu-id="65748-158">이 격리로 인해 태스크는 실행 순서와 관련된 패키지 내에서의 태스크 위치를 알 수 없으므로 런타임에서 호출될 때만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-158">Because of this isolation, the task is unaware of its location in the package with regard to its execution order, and runs only when it is called by the runtime.</span></span> <span data-ttu-id="65748-159">이 아키텍처를 통해 실행 중 태스크에서 패키지를 수정할 때 발생할 수 있는 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-159">This architecture prevents problems that can occur when tasks modify the package during execution.</span></span> <span data-ttu-id="65748-160">격리된 태스크에서는 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드에 매개 변수로 지정된 개체를 통해서만 패키지의 다른 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-160">The task is provided access to the other objects in the package only through the objects supplied to it as parameters in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="65748-161">태스크에서는 이러한 매개 변수를 통해 패키지의 안정성을 보장하는 데 필요한 격리 상태를 유지하면서 이벤트를 발생시키고, 이벤트 로그에 항목을 기록하고, 변수 컬렉션에 액세스하고, 데이터 원본에 대한 연결을 트랜잭션에 참여시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-161">These parameters let tasks raise events, write entries to the event log, access the variables collection, and enlist connections to data sources in transactions, while still maintaining the isolation that is necessary to guarantee the stability and reliability of the package.</span></span>

 <span data-ttu-id="65748-162">다음 표에서는 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드에서 태스크에 제공되는 매개 변수를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-162">The following table lists the parameters provided to the task in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>

|<span data-ttu-id="65748-163">매개 변수</span><span class="sxs-lookup"><span data-stu-id="65748-163">Parameter</span></span>|<span data-ttu-id="65748-164">Description</span><span class="sxs-lookup"><span data-stu-id="65748-164">Description</span></span>|
|---------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|<span data-ttu-id="65748-165">태스크에서 사용할 수 있는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체의 컬렉션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-165">Contains a collection of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects available to the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|<span data-ttu-id="65748-166">태스크에서 사용할 수 있는 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-166">Contains the variables available to the task.</span></span> <span data-ttu-id="65748-167">태스크에서는 변수를 직접 사용하는 것이 아니라 VariableDispenser를 통해 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-167">The tasks use variables through the VariableDispenser; the tasks do not use variables directly.</span></span> <span data-ttu-id="65748-168">VariableDispenser는 변수를 잠그거나 잠금 해제하고 교착 상태나 덮어쓰기를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-168">The variable dispenser locks and unlocks variables, and prevents deadlocks or overwrites.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|<span data-ttu-id="65748-169">태스크에서 런타임 엔진에 이벤트를 발생시키기 위해 호출하는 메서드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-169">Contains the methods called by the task to raise events to the run-time engine.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|<span data-ttu-id="65748-170">태스크에서 이벤트 로그에 항목을 기록하는 데 사용하는 메서드 및 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-170">Contains methods and properties used by the task to write entries to the event log.</span></span>|
|<span data-ttu-id="65748-171">Object</span><span class="sxs-lookup"><span data-stu-id="65748-171">Object</span></span>|<span data-ttu-id="65748-172">해당 컨테이너가 포함된 트랜잭션 개체가 있는 경우 이를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-172">Contains the transaction object that the container is a part of, if any.</span></span> <span data-ttu-id="65748-173">이 값은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 메서드에 매개 변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-173">This value is passed as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object.</span></span>|

### <a name="providing-execution-feedback"></a><span data-ttu-id="65748-174">실행 피드백 제공</span><span class="sxs-lookup"><span data-stu-id="65748-174">Providing Execution Feedback</span></span>
 <span data-ttu-id="65748-175">태스크에서는 해당 코드를 `try/catch` 블록에 래핑하여 런타임 엔진에 예외가 발생하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-175">Tasks wrap their code in `try/catch` blocks to prevent exceptions from being raised to the run-time engine.</span></span> <span data-ttu-id="65748-176">이렇게 하면 패키지 실행이 끝까지 완료되며 예기치 않게 중지되는 경우가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-176">This ensures that the package finishes execution and does not stop unexpectedly.</span></span> <span data-ttu-id="65748-177">그러나 런타임 엔진에서는 태스크 실행 중 발생할 수 있는 오류 조건을 처리하기 위한 다른 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-177">However, the run-time engine provides other mechanisms for handling error conditions that can occur during the execution of a task.</span></span> <span data-ttu-id="65748-178">이러한 메커니즘에는 오류 및 경고 메시지 게시, <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 구조의 값 반환, 메시지 게시, <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 값 반환 및 <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> 속성을 통한 태스크 실행 결과에 대한 정보 공개 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="65748-178">These include posting error and warning messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> structure, posting messages, returning the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value, and disclosing information about the results of task execution through the <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> property.</span></span>

 <span data-ttu-id="65748-179"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 인터페이스에는 태스크에서 런타임 엔진에 오류 및 경고 메시지를 게시하기 위해 호출할 수 있는 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-179">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods, which can be called by the task to post error and warning messages to the run-time engine.</span></span> <span data-ttu-id="65748-180">두 메서드에는 오류 코드, 원본 구성 요소, 설명, 도움말 파일 및 도움말 컨텍스트 정보와 같은 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-180">Both methods require parameters such as the error code, source component, description, Help file, and help context information.</span></span> <span data-ttu-id="65748-181">런타임에서는 태스크의 구성에 따라 이벤트 및 중단점을 발생시키거나 이벤트 로그에 정보를 기록하는 방식으로 이러한 메시지에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-181">Depending on the configuration of the task, the runtime responds to these messages by raising events and breakpoints, or by writing information to the event log.</span></span>

 <span data-ttu-id="65748-182"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서는 실행 결과에 대한 추가 정보를 제공하는 데 사용할 수 있는 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 속성도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-182">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> also provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property that can be used to provide additional information about the results of execution.</span></span> <span data-ttu-id="65748-183">예를 들어 태스크에서 `Execute` 메서드 실행 중 테이블의 행을 삭제할 경우 삭제한 행 수를 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 속성의 값으로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-183">For example, if a task deletes rows from a table as part of its `Execute` method, it might return the number of rows deleted as the value of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property.</span></span> <span data-ttu-id="65748-184">또한 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서는 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> 속성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-184">In addition, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> property.</span></span> <span data-ttu-id="65748-185">이 속성을 통해 사용자는 태스크에서 반환된 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A>를 태스크에 표시되는 변수에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-185">This property lets the user map the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> returned from the task to any variable visible to the task.</span></span> <span data-ttu-id="65748-186">그런 다음 지정한 변수를 사용하여 태스크 간에 선행 제약 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65748-186">The specified variable can then be used to establish precedence constraints between tasks.</span></span>

### <a name="execution-example"></a><span data-ttu-id="65748-187">실행 예</span><span class="sxs-lookup"><span data-stu-id="65748-187">Execution Example</span></span>
 <span data-ttu-id="65748-188">다음 코드 예제서는 `Execute` 메서드의 구현과 재정의된 `ExecutionValue` 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65748-188">The following code example demonstrates an implementation of the `Execute` method, and shows an overridden `ExecutionValue` property.</span></span> <span data-ttu-id="65748-189">태스크에서는 해당 태스크의 `fileName` 속성으로 지정된 파일을 삭제하고,</span><span class="sxs-lookup"><span data-stu-id="65748-189">The task deletes the file that is specified by the `fileName` property of the task.</span></span> <span data-ttu-id="65748-190">파일이 없거나 `fileName` 속성이 빈 문자열인 경우에는 경고를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="65748-190">The task posts a warning if the file does not exist, or if the `fileName` property is an empty string.</span></span> <span data-ttu-id="65748-191">또한 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 속성에서 `Boolean` 값을 반환하여 파일이 삭제되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65748-191">The task returns a `Boolean` value in the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property to indicate whether the file was deleted.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string fileName = "";
  private bool fileDeleted = false;

  public override DTSExecResult Execute(Connections cons,
     VariableDispenser vars, IDTSComponentEvents events,
     IDTSLogging log, Object txn)
  {
    try
    {
      if (this.fileName == "")
      {
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);
        this.fileDeleted = false;
      }
      else
      {
        if (System.IO.File.Exists(this.fileName))
        {
          System.IO.File.Delete(this.fileName);
          this.fileDeleted = true;
        }
        else
          this.fileDeleted = false;
      }
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string FileName
  {
    get { return this.fileName; }
    set { this.fileName = value; }
  }
  public override object ExecutionValue
  {
    get { return this.fileDeleted; }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _fileName As String = ""
  Private _fileDeleted As Boolean = False

  Public Overrides Function Execute(ByVal cons As Connections, _
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult

    Try
      If Me._fileName = "" Then
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)
        Me._fileDeleted = False
      Else
        If System.IO.File.Exists(Me._fileName) Then
          System.IO.File.Delete(Me._fileName)
          Me._fileDeleted = True
        Else
          Me._fileDeleted = False
        End If
      End If
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property FileName() As String
    Get
      Return Me._fileName
    End Get
    Set(ByVal Value As String)
      Me._fileName = Value
    End Set
  End Property

  Public Overrides ReadOnly Property ExecutionValue() As Object
    Get
      Return Me._fileDeleted
    End Get
  End Property

End Class
```

<span data-ttu-id="65748-192">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="65748-192">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="65748-193">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="65748-193">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="65748-194">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="65748-194">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="65748-195">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="65748-195">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="65748-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65748-196">See Also</span></span>
 <span data-ttu-id="65748-197">사용자 지정 [작업 만들기](creating-a-custom-task.md) 사용자 지정 태스크 [코딩](coding-a-custom-task.md) 사용자 지정 태스크 [에 대 한 사용자 인터페이스 개발](developing-a-user-interface-for-a-custom-task.md)</span><span class="sxs-lookup"><span data-stu-id="65748-197">[Creating a Custom Task](creating-a-custom-task.md) [Coding a Custom Task](coding-a-custom-task.md) [Developing a User Interface for a Custom Task](developing-a-user-interface-for-a-custom-task.md)</span></span>


