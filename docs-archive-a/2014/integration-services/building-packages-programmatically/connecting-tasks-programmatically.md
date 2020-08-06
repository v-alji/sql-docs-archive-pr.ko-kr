---
title: 프로그래밍 방식으로 태스크 연결 | Microsoft Docs
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
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5aeeb70ed5741cc7372fdfc63e637fd53d932f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649640"
---
# <a name="connecting-tasks-programmatically"></a><span data-ttu-id="6f54b-102">프로그래밍 방식으로 태스크 연결</span><span class="sxs-lookup"><span data-stu-id="6f54b-102">Connecting Tasks Programmatically</span></span>
  <span data-ttu-id="6f54b-103">개체 모델에서 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 클래스가 나타내는 선행 제약 조건은 패키지에서 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 개체가 실행되는 순서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-103">A precedence constraint, represented in the object model by the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> class, establishes the order in which <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects run in a package.</span></span> <span data-ttu-id="6f54b-104">선행 제약 조건을 사용하면 패키지의 컨테이너 및 태스크 실행이 이전 태스크 또는 컨테이너의 실행 결과에 따라 결정되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-104">The precedence constraint allows the execution of the containers and tasks in a package to be dependent on the result of the execution of a previous task or container.</span></span> <span data-ttu-id="6f54b-105">선행 제약 조건은 컨테이너 개체에서 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> 메서드를 호출하여 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> 개체 쌍 간에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-105">Precedence constraints are established between pairs of <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects by calling the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> collection on the container object.</span></span> <span data-ttu-id="6f54b-106">두 개의 실행 개체 사이에 제약 조건을 만든 후 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> 속성을 설정하여 제약 조건에 정의된 두 번째 실행 파일을 실행하기 위한 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-106">After you create a constraint between two executable objects, you set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> property to establish the criteria for executing the second executable defined in the constraint.</span></span>  
  
 <span data-ttu-id="6f54b-107">다음 표에서 설명하는 것처럼 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A> 속성에 지정하는 값에 따라 단일 선행 제약 조건에 제약 조건과 식을 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-107">You can use both a constraint and an expression in a single precedence constraint, depending on the value that you specify for the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A> property, as described in the following table:</span></span>  
  
|<span data-ttu-id="6f54b-108">EvalOp 속성 값</span><span class="sxs-lookup"><span data-stu-id="6f54b-108">Value of the EvalOp property</span></span>|<span data-ttu-id="6f54b-109">Description</span><span class="sxs-lookup"><span data-stu-id="6f54b-109">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|<span data-ttu-id="6f54b-110">실행 결과에 따라 제약 조건이 지정된 컨테이너 또는 태스크의 실행 여부가 결정되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-110">Specifies that the execution outcome determines whether the constrained container or task runs.</span></span> <span data-ttu-id="6f54b-111"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 속성을 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 열거형에서 원하는 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-111">Set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> to the desired value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|<span data-ttu-id="6f54b-112">식의 값에 따라 제약 조건이 지정된 컨테이너 또는 태스크의 실행 여부가 결정되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-112">Specifies that the value of an expression determines whether the constrained container or task runs.</span></span> <span data-ttu-id="6f54b-113"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-113">Set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|<span data-ttu-id="6f54b-114">제약 조건 결과가 발생해야 하며 식에서 제약 조건이 지정된 컨테이너 또는 태스크의 실행을 평가해야 하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-114">Specifies that the constraint outcome must occur and the expression must evaluate for the constrained container or task to run.</span></span> <span data-ttu-id="6f54b-115"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> 속성과 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 속성을 모두 설정하고 해당 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> 속성을 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-115">Set both the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> properties of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, and set its <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> property to `true`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|<span data-ttu-id="6f54b-116">제약 조건 결과가 발생해야 하거나 식에서 제약 조건이 지정된 컨테이너 또는 태스크의 실행을 평가해야 하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-116">Specifies that either the constraint outcome must occur, or the expression must evaluate, for the constrained container or task to run.</span></span> <span data-ttu-id="6f54b-117"><xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> 속성과 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 속성을 모두 설정하고 해당 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> 속성을 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-117">Set both the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> properties of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, and set its <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> property to `false`.</span></span>|  
  
 <span data-ttu-id="6f54b-118">다음 코드 예제에서는 패키지에 두 개의 태스크를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-118">The following code sample demonstrates adding two tasks to a package.</span></span> <span data-ttu-id="6f54b-119">두 태스크 사이에는 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>가 만들어지므로 첫 번째 태스크가 완료될 때까지 두 번째 태스크는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f54b-119">A <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> is created between them that prevents the second task from running until the first task finishes.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="6f54b-120">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6f54b-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6f54b-121">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6f54b-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6f54b-122">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6f54b-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6f54b-123">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6f54b-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f54b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f54b-124">See Also</span></span>  
 [<span data-ttu-id="6f54b-125">프로그래밍 방식으로 데이터 흐름 태스크 추가</span><span class="sxs-lookup"><span data-stu-id="6f54b-125">Adding the Data Flow Task Programmatically</span></span>](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
