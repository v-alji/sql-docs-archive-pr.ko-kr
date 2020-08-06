---
title: 프로그래밍 방식으로 변수 사용 | Microsoft Docs
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
- System namespace
- scope [Integration Services]
- variables [Integration Services], programmatically
- configuration files [Integration Services]
- Variables collection
- User namespace
- custom variables [Integration Services]
- variables [Integration Services], customizing
ms.assetid: c4b76a3d-94ca-4a8e-bb45-cb8bd0ea3ec1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c903ee6adb8989eaeb93efbe943eca93c73eae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738680"
---
# <a name="working-with-variables-programmatically"></a><span data-ttu-id="aafb4-102">프로그래밍 방식으로 변수 사용</span><span class="sxs-lookup"><span data-stu-id="aafb4-102">Working with Variables Programmatically</span></span>
  <span data-ttu-id="aafb4-103">변수는 패키지, 컨테이너, 태스크 및 이벤트 처리기에서 동적으로 값을 설정하고 프로세스를 제어하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-103">Variables are a way to dynamically set values and control processes in packages, containers, tasks, and event handlers.</span></span> <span data-ttu-id="aafb4-104">선행 제약 조건에서 변수를 사용하여 다른 태스크로의 데이터 흐름 방향을 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-104">Variables can also be used by precedence constraints to control the direction of the flow of data to different tasks.</span></span> <span data-ttu-id="aafb4-105">다음과 같은 다양한 용도로 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-105">Variables have a variety of uses:</span></span>

-   <span data-ttu-id="aafb4-106">런타임에 패키지의 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-106">Update properties of a package at run time.</span></span>

-   <span data-ttu-id="aafb4-107">런타임에 Transact-SQL 문의 매개 변수 값을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-107">Populate parameter values for Transact-SQL statements at run time.</span></span>

-   <span data-ttu-id="aafb4-108">Foreach 루프의 흐름을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-108">Control the flow of a Foreach loop.</span></span> <span data-ttu-id="aafb4-109">자세한 내용은 [제어 흐름에 열거 추가](../control-flow/control-flow.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-109">For more information, see [Add Enumeration to a Control Flow](../control-flow/control-flow.md).</span></span>

-   <span data-ttu-id="aafb4-110">선행 제약 조건의 식에 사용하여 선행 제약 조건을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-110">Control a precedence constraint by its use in an expression.</span></span> <span data-ttu-id="aafb4-111">선행 제약 조건의 제약 조건 정의에는 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-111">A precedence constraint can include variables in the constraint definition.</span></span> <span data-ttu-id="aafb4-112">자세한 내용은 [선행 제약 조건에 식 추가](../control-flow/precedence-constraints.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-112">For more information, see [Add Expressions to Precedence Constraints](../control-flow/precedence-constraints.md).</span></span>

-   <span data-ttu-id="aafb4-113">For 루프 컨테이너의 조건부 반복을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-113">Control the conditional repeat of a For Loop container.</span></span> <span data-ttu-id="aafb4-114">자세한 내용은 [제어 흐름에 반복 추가](../add-iteration-to-a-control-flow.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-114">For more information, see [Add Iteration to a Control Flow](../add-iteration-to-a-control-flow.md).</span></span>

-   <span data-ttu-id="aafb4-115">변수 값이 포함된 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-115">Build expressions that include variable values.</span></span>

-   <span data-ttu-id="aafb4-116">사용자 지정 변수는 패키지, **Foreach 루프** 컨테이너, **For 루프** 컨테이너, **시퀀스** 컨테이너, TaskHost 및 이벤트 처리기와 같은 모든 컨테이너 유형에 대해 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-116">You can create custom variables for all container types: packages, **Foreach Loop** containers, **For Loop** containers, **Sequence** containers, TaskHosts, and event handlers.</span></span> <span data-ttu-id="aafb4-117">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-117">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>

## <a name="scope"></a><span data-ttu-id="aafb4-118">범위</span><span class="sxs-lookup"><span data-stu-id="aafb4-118">Scope</span></span>
 <span data-ttu-id="aafb4-119">각 컨테이너에는 고유한 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 컬렉션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-119">Each container has its own <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection.</span></span> <span data-ttu-id="aafb4-120">새 변수를 만들면 해당 변수는 부모 컨테이너의 범위 내에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-120">When a new variable is created, it is within the scope of its parent container.</span></span> <span data-ttu-id="aafb4-121">패키지 컨테이너는 컨테이너 계층 구조의 최상위에 있으므로 패키지 범위의 변수는 전역 변수와 같은 기능을 수행하며 해당 패키지 내의 모든 컨테이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-121">Because the package container is at the top of the container hierarchy, variables with package scope function like global variables, and are visible to all containers within the package.</span></span> <span data-ttu-id="aafb4-122">또한 컨테이너의 자식 컨테이너에서는 변수 이름이나 컬렉션에서의 변수 인덱스를 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 컬렉션을 통해 컨테이너의 변수 컬렉션에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-122">The collection of variables for the container can also be accessed by the children of the container through the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection, by using either the variable name or the variable's index in the collection.</span></span>

 <span data-ttu-id="aafb4-123">변수의 표시 범위는 하향식으로 결정되므로 패키지 수준에서 선언된 변수는 해당 패키지의 모든 컨테이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-123">Because the visibility of a variable is scoped from the top down, variables declared at the package level are visible to all the containers in the package.</span></span> <span data-ttu-id="aafb4-124">따라서 컨테이너의 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 컬렉션에는 해당 컨테이너의 변수뿐 아니라 부모 컨테이너에 속하는 모든 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-124">Therefore, the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection on a container includes all the variables that belong to its parent in addition to its own variables</span></span>

 <span data-ttu-id="aafb4-125">반면, 태스크에 포함된 변수는 범위 및 표시 여부가 제한적이므로 해당 태스크에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-125">Conversely, the variables that are contained in a task are limited in scope and visibility, and are only visible to the task.</span></span>

 <span data-ttu-id="aafb4-126">패키지에서 다른 패키지를 실행할 경우 호출하는 패키지의 범위에 정의된 변수를 호출되는 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-126">If a package runs other packages, the variables defined in the scope of the calling package are available to the called package.</span></span> <span data-ttu-id="aafb4-127">단, 같은 이름의 변수가 호출되는 패키지에도 있는 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-127">The only exception occurs when a same-named variable exists in the called package.</span></span> <span data-ttu-id="aafb4-128">이러한 충돌이 발생할 경우에는 호출되는 패키지의 변수 값이 호출하는 패키지의 값보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-128">When this collision occurs, the variable value in the called package overrides the value from the calling package.</span></span> <span data-ttu-id="aafb4-129">반대로 호출되는 패키지의 범위에 정의된 변수를 호출하는 패키지에서 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-129">Variables defined in the scope of the called package are never available back to the calling package.</span></span>

 <span data-ttu-id="aafb4-130">다음 코드 예에서는 패키지 범위에서 프로그래밍 방식으로 `myCustomVar` 변수를 만든 다음 해당 패키지에 표시된 모든 변수를 반복하여 각 변수의 이름, 데이터 형식 및 값을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-130">The following code example programmatically creates a variable, `myCustomVar`, at the package scope, and then iterates through all the variables visible to the package, printing their name, data type, and value.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Application app = new Application();
      // Load a sample package that contains a variable that sets the file name.
      Package pkg = app.LoadPackage(
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +
        @"\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx",
        null);
      Variables pkgVars = pkg.Variables;
      Variable myVar = pkg.Variables.Add("myCustomVar", false, "User", "3");
      foreach (Variable pkgVar in pkgVars)
      {
        Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name,
          pkgVar.DataType, pkgVar.Value.ToString());
      }
      Console.Read();
    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim app As Application = New Application()
    ' Load a sample package that contains a variable that sets the file name.
    Dim pkg As Package = app.LoadPackage( _
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _
      "\Package Samples\CaptureDataLineage Sample\CaptureDataLineage\CaptureDataLineage.dtsx", _
      Nothing)
    Dim pkgVars As Variables = pkg.Variables
    Dim myVar As Variable = pkg.Variables.Add("myCustomVar", False, "User", "3")
    Dim pkgVar As Variable
    For Each pkgVar In pkgVars
      Console.WriteLine("Variable: {0}, {1}, {2}", pkgVar.Name, _
        pkgVar.DataType, pkgVar.Value.ToString())
    Next
    Console.Read()

  End Sub

End Module
```

 <span data-ttu-id="aafb4-131">**샘플 출력:**</span><span class="sxs-lookup"><span data-stu-id="aafb4-131">**Sample Output:**</span></span>

 `Variable: CancelEvent, Int32, 0`

 `Variable: CreationDate, DateTime, 4/18/2003 11:57:00 AM`

 `Variable: CreatorComputerName, String,`

 `Variable: CreatorName, String,`

 `Variable: ExecutionInstanceGUID, String, {237AB5A4-7E59-4FC9-8D61-E8F20363DF25}`

 `Variable: FileName, String, Junk`

 `Variable: InteractiveMode, Boolean, False`

 `Variable: LocaleID, Int32, 1033`

 `Variable: MachineName, String, MYCOMPUTERNAME`

 `Variable: myCustomVar, String, 3`

 `Variable: OfflineMode, Boolean, False`

 `Variable: PackageID, String, {F0D2E396-A6A5-42AE-9467-04CE946A810C}`

 `Variable: PackageName, String, DTSPackage1`

 `Variable: StartTime, DateTime, 1/28/2005 7:55:39 AM`

 `Variable: UserName, String, <domain>\<userid>`

 `Variable: VersionBuild, Int32, 198`

 `Variable: VersionComments, String,`

 `Variable: VersionGUID, String, {90E105B4-B4AF-4263-9CBD-C2050C2D6148}`

 `Variable: VersionMajor, Int32, 1`

 `Variable: VersionMinor, Int32, 0`

 <span data-ttu-id="aafb4-132">범위가 **System** 네임스페이스인 모든 변수는 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-132">Notice that all the variables scoped in the **System** namespace are available to the package.</span></span> <span data-ttu-id="aafb4-133">자세한 내용은 [System Variables](../system-variables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-133">For more information, see [System Variables](../system-variables.md).</span></span>

## <a name="namespaces"></a><span data-ttu-id="aafb4-134">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="aafb4-134">Namespaces</span></span>
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="aafb4-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)])에서는 변수가 존재하는 두 개의 기본 네임스페이스인 **User** 및 **System** 네임스페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) provides two default namespaces where variables reside; **User** and **System** namespaces.</span></span> <span data-ttu-id="aafb4-136">기본적으로 개발자가 만드는 모든 사용자 지정 변수는 **User** 네임스페이스에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-136">By default, any custom variable created by the developer is added to the **User** namespace.</span></span> <span data-ttu-id="aafb4-137">시스템 변수는 **System** 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-137">System variables reside in the **System** namespace.</span></span> <span data-ttu-id="aafb4-138">**User** 네임스페이스 외의 추가 네임스페이스를 만들어 사용자 지정 변수를 저장하거나, **User** 네임스페이스의 이름을 변경할 수는 있지만 **System** 네임스페이스의 변수를 추가 또는 수정하거나, 시스템 변수를 다른 네임스페이스에 할당할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-138">You can create additional namespaces other than the **User** namespace to hold custom variables, and you can change the name of the **User** namespace, but you cannot add or modify variables in the **System** namespace, or assign system variables to a different namespace.</span></span>

 <span data-ttu-id="aafb4-139">사용할 수 있는 시스템 변수는 컨테이너 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-139">The system variables that are available differ depending on the container type.</span></span> <span data-ttu-id="aafb4-140">패키지, 컨테이너, 태스크 및 이벤트 처리기에서 사용할 수 있는 시스템 변수의 목록은 [시스템 변수](../system-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-140">For a list of the system variables available to packages, containers, tasks, and event handlers, see [System Variables](../system-variables.md).</span></span>

## <a name="value"></a><span data-ttu-id="aafb4-141">값</span><span class="sxs-lookup"><span data-stu-id="aafb4-141">Value</span></span>
 <span data-ttu-id="aafb4-142">사용자 지정 변수의 값은 리터럴 또는 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-142">The value of a custom variable can be a literal or an expression:</span></span>

-   <span data-ttu-id="aafb4-143">변수에 리터럴 값을 포함하려면 변수의 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 속성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-143">If you want the variable to contain a literal value, set the value of its <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property.</span></span>

-   <span data-ttu-id="aafb4-144">식의 결과를 값으로 사용할 수 있도록 변수에 식을 포함하려면 변수의 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> 속성을 `true`로 설정하고 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> 속성에서 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-144">If you want the variable to contain an expression, so that you can use the results of the expression as its value, set the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> property of the variable to `true`, and provide an expression in the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Expression%2A> property.</span></span> <span data-ttu-id="aafb4-145">런타임에는 이 식이 계산되고 식 결과가 변수 값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-145">At run time, the expression is evaluated, and the result of the expression is used as the value of the variable.</span></span> <span data-ttu-id="aafb4-146">예를 들어 변수의 식 속성이 `"100 * 2""100 * 2"`이면 이 변수는 값 200으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-146">For example, if the expression property of a variable is `"100 * 2""100 * 2"`, the variable evaluates to a value of 200.</span></span>

 <span data-ttu-id="aafb4-147">변수의 경우에는 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> 값을 명시적으로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-147">For a variable, you cannot explicitly set the value of its <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A>.</span></span> <span data-ttu-id="aafb4-148"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> 값은 변수에 할당된 초기 값에서 유추되며 이후에는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-148">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.DataType%2A> value is inferred from the initial value assigned to the variable, and cannot be changed afterward.</span></span> <span data-ttu-id="aafb4-149">변수 데이터 형식에 대한 자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-149">For more information about variable data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>

 <span data-ttu-id="aafb4-150">다음 코드 예에서는 새 변수를 만들고, <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A>을 `true`로 설정하고, 변수의 식 속성에 `"100 * 2"` 식을 할당한 다음, 변수 값을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-150">The following code example creates a new variable, sets <xref:Microsoft.SqlServer.Dts.Runtime.Variable.EvaluateAsExpression%2A> to `true`, assigns the expression `"100 * 2"` to the expression property of the variable, and then outputs the value of the variable.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package pkg = new Package();
      Variable v100 = pkg.Variables.Add("myVar", false, "", 1);
      v100.EvaluateAsExpression = true;
      v100.Expression = "100 * 2";
      Console.WriteLine("Expression for myVar: {0}", 
        v100.Properties["Expression"].GetValue(v100));
      Console.WriteLine("Value of myVar: {0}", v100.Value.ToString());
      Console.Read();
    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim pkg As Package = New Package
    Dim v100 As Variable = pkg.Variables.Add("myVar", False, "", 1)
    v100.EvaluateAsExpression = True
    v100.Expression = "100 * 2"
    Console.WriteLine("Expression for myVar: {0}", _
      v100.Properties("Expression").GetValue(v100))
    Console.WriteLine("Value of myVar: {0}", v100.Value.ToString)
    Console.Read()

  End Sub

End Module
```

 <span data-ttu-id="aafb4-151">**샘플 출력:**</span><span class="sxs-lookup"><span data-stu-id="aafb4-151">**Sample Output:**</span></span>

 `Expression for myVar: 100 * 2`

 `Value of myVar: 200`

 <span data-ttu-id="aafb4-152">식은 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 식 구문을 사용하는 유효한 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-152">The expression must be a valid expression that uses the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="aafb4-153">변수 식에는 식 구문에서 제공하는 연산자와 함수뿐 아니라 리터럴도 사용할 수 있지만 식에서 다른 변수 또는 열을 참조할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-153">Literals are permitted in variable expressions, in addition to the operators and functions that the expression syntax provides, but expressions cannot reference other variables or columns.</span></span> <span data-ttu-id="aafb4-154">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md)가 될 때까지 워크플로를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-154">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="aafb4-155">구성 파일</span><span class="sxs-lookup"><span data-stu-id="aafb4-155">Configuration Files</span></span>
 <span data-ttu-id="aafb4-156">구성 파일에 사용자 지정 변수가 포함된 경우 런타임에 해당 변수를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-156">If a configuration file includes a custom variable, the variable can be updated at run time.</span></span> <span data-ttu-id="aafb4-157">즉, 패키지를 실행할 때 패키지의 원래 변수 값을 구성 파일의 새 값으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-157">What this means is that when the package runs, the value of the variable originally in the package is replaced with a new value from the configuration file.</span></span> <span data-ttu-id="aafb4-158">이 기술은 패키지가 각기 다른 변수 값이 필요한 여러 서버에 배포된 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-158">This replacement technique is useful when a package is deployed to multiple servers that require different variable values.</span></span> <span data-ttu-id="aafb4-159">예를 들어 변수는 **Foreach 루프** 컨테이너가 워크플로를 반복하는 횟수를 지정하거나, 오류가 발생할 경우 이벤트 처리기에서 보내는 전자 메일의 받는 사람을 나열하거나, 패키지가 실패한 것으로 처리되기 전에 발생할 수 있는 오류 횟수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-159">For example, a variable can specify the number of times a **Foreach Loop** container repeats its workflow, or list the recipients that an event handler sends e-mail to when an error is raised, or change the number of errors that can occur before the package fails.</span></span> <span data-ttu-id="aafb4-160">이러한 변수는 각 환경의 구성 파일에서 동적으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-160">These variables are dynamically provided in configuration files for each environment.</span></span> <span data-ttu-id="aafb4-161">따라서 구성 파일에는 읽기/쓰기가 가능한 변수만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-161">Therefore, only variables that are read/write are allowed in configuration files.</span></span> <span data-ttu-id="aafb4-162">자세한 내용은 [패키지 구성 만들기](../create-package-configurations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-162">For more information, see [Create Package Configurations](../create-package-configurations.md).</span></span>

<span data-ttu-id="aafb4-163">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="aafb4-163">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="aafb4-164">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-164">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="aafb4-165">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-165">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="aafb4-166">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="aafb4-166">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="aafb4-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aafb4-167">See Also</span></span>
 <span data-ttu-id="aafb4-168">[Integration Services &#40;SSIS&#41; 변수가](../integration-services-ssis-variables.md) [패키지에서 변수를 사용](../use-variables-in-packages.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="aafb4-168">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) [Use Variables in Packages](../use-variables-in-packages.md)</span></span>


