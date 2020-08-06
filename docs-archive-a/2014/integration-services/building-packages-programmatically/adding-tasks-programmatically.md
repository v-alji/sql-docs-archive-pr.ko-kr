---
title: 프로그래밍 방식으로 태스크 추가 | Microsoft Docs
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
- tasks [Integration Services], packages
- adding package tasks
ms.assetid: 5d4652d5-228c-4238-905c-346dd8503fdf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa61eb2fb87f45fe5b534b96280b8b4e2c21788d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649647"
---
# <a name="adding-tasks-programmatically"></a><span data-ttu-id="2cd9d-102">프로그래밍 방식으로 태스크 추가</span><span class="sxs-lookup"><span data-stu-id="2cd9d-102">Adding Tasks Programmatically</span></span>
  <span data-ttu-id="2cd9d-103">런타임 엔진에서 다음과 같은 유형의 개체에 태스크를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-103">Tasks can be added to the following types of objects in the run-time engine:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Package>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Sequence>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>  
  
 <span data-ttu-id="2cd9d-104">이러한 클래스는 컨테이너로 간주되며 모두 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> 속성을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-104">These classes are considered containers, and they all inherit the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> property.</span></span> <span data-ttu-id="2cd9d-105">컨테이너에는 해당 컨테이너를 실행하는 동안 런타임에서 처리할 수 있는 실행 개체인 태스크의 컬렉션이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-105">Containers can contain a collection of tasks, which are executable objects processed by the runtime during execution of the container.</span></span> <span data-ttu-id="2cd9d-106">컬렉션에 있는 개체의 실행 순서는 컨테이너의 각 태스크에 설정된 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-106">The order of execution of the objects in the collection is determined any <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> set on each task in the containers.</span></span> <span data-ttu-id="2cd9d-107">선행 제약 조건을 사용하면 컬렉션에 있는 <xref:Microsoft.SqlServer.Dts.Runtime.Executable>의 성공, 실패 또는 완료 상태에 따라 실행을 분기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-107">Precedence constraints enable execution branching based on the success, failure, or completion of an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> in the collection.</span></span>  
  
 <span data-ttu-id="2cd9d-108">각 컨테이너에는 개별 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 개체가 들어 있는 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 컬렉션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-108">Each container has an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection that contains the individual <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects.</span></span> <span data-ttu-id="2cd9d-109">각 실행 태스크는 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> 메서드와 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> 메서드를 상속하고 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-109">Each executable task inherits and implements the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> method and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> method.</span></span> <span data-ttu-id="2cd9d-110">런타임 엔진에서는 이 두 메서드를 호출하여 각 <xref:Microsoft.SqlServer.Dts.Runtime.Executable>을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-110">These two methods are called by the run-time engine to process each <xref:Microsoft.SqlServer.Dts.Runtime.Executable>.</span></span>  
  
 <span data-ttu-id="2cd9d-111">패키지에 태스크를 추가하려면 기존 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 컬렉션이 있는 컨테이너가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-111">To add a task to a package, you need a container with an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> existing collection.</span></span> <span data-ttu-id="2cd9d-112">대부분의 경우 컬렉션에 추가할 태스크는 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-112">Most of the time, the task that you will add to the collection is a package.</span></span> <span data-ttu-id="2cd9d-113">새 태스크 실행 파일을 해당 컨테이너의 컬렉션에 추가하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-113">To add the new task executable into the collection for that container, you call the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method .</span></span> <span data-ttu-id="2cd9d-114">이 메서드에는 추가할 태스크의 CLSID, PROGID, STOCK 모니커 또는 <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A>이 들어 있는 단일 문자열 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-114">The method has a single parameter, a string, that contains the CLSID, PROGID, STOCK moniker, or <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A> of the task you are adding.</span></span>  
  
## <a name="task-names"></a><span data-ttu-id="2cd9d-115">태스크 이름</span><span class="sxs-lookup"><span data-stu-id="2cd9d-115">Task Names</span></span>  
 <span data-ttu-id="2cd9d-116">태스크는 이름이나 ID로 지정할 수 있지만 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 메서드에서 가장 자주 사용되는 매개 변수는 `STOCK` 모니커입니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-116">Although you can specify a task by name or by ID, the `STOCK` moniker is the parameter used most often in the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method.</span></span> <span data-ttu-id="2cd9d-117">`STOCK` 모니터로 식별된 실행 파일에 태스크를 추가하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-117">To add a task to an executable identified by the `STOCK` moniker, use the following syntax:</span></span>  
  
```csharp  
Executable exec = package.Executables.Add("STOCK:BulkInsertTask");  
  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add("STOCK:BulkInsertTask")  
  
```  
  
 <span data-ttu-id="2cd9d-118">다음 목록에서는 `STOCK` 모니커 다음에 사용되는 각 태스크의 이름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-118">The following list shows the names for each task that are used after the `STOCK` moniker.</span></span>  
  
-   <span data-ttu-id="2cd9d-119">ActiveXScriptTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-119">ActiveXScriptTask</span></span>  
  
-   <span data-ttu-id="2cd9d-120">BulkInsertTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-120">BulkInsertTask</span></span>  
  
-   <span data-ttu-id="2cd9d-121">ExecuteProcessTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-121">ExecuteProcessTask</span></span>  
  
-   <span data-ttu-id="2cd9d-122">ExecutePackageTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-122">ExecutePackageTask</span></span>  
  
-   <span data-ttu-id="2cd9d-123">Exec80PackageTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-123">Exec80PackageTask</span></span>  
  
-   <span data-ttu-id="2cd9d-124">FileSystemTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-124">FileSystemTask</span></span>  
  
-   <span data-ttu-id="2cd9d-125">FTPTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-125">FTPTask</span></span>  
  
-   <span data-ttu-id="2cd9d-126">MSMQTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-126">MSMQTask</span></span>  
  
-   <span data-ttu-id="2cd9d-127">PipelineTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-127">PipelineTask</span></span>  
  
-   <span data-ttu-id="2cd9d-128">ScriptTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-128">ScriptTask</span></span>  
  
-   <span data-ttu-id="2cd9d-129">SendMailTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-129">SendMailTask</span></span>  
  
-   <span data-ttu-id="2cd9d-130">SQLTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-130">SQLTask</span></span>  
  
-   <span data-ttu-id="2cd9d-131">TransferStoredProceduresTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-131">TransferStoredProceduresTask</span></span>  
  
-   <span data-ttu-id="2cd9d-132">TransferLoginsTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-132">TransferLoginsTask</span></span>  
  
-   <span data-ttu-id="2cd9d-133">TransferErrorMessagesTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-133">TransferErrorMessagesTask</span></span>  
  
-   <span data-ttu-id="2cd9d-134">TransferJobsTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-134">TransferJobsTask</span></span>  
  
-   <span data-ttu-id="2cd9d-135">TransferObjectsTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-135">TransferObjectsTask</span></span>  
  
-   <span data-ttu-id="2cd9d-136">TransferDatabaseTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-136">TransferDatabaseTask</span></span>  
  
-   <span data-ttu-id="2cd9d-137">WebServiceTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-137">WebServiceTask</span></span>  
  
-   <span data-ttu-id="2cd9d-138">WmiDataReaderTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-138">WmiDataReaderTask</span></span>  
  
-   <span data-ttu-id="2cd9d-139">WmiEventWatcherTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-139">WmiEventWatcherTask</span></span>  
  
-   <span data-ttu-id="2cd9d-140">XMLTask</span><span class="sxs-lookup"><span data-stu-id="2cd9d-140">XMLTask</span></span>  
  
 <span data-ttu-id="2cd9d-141">보다 명시적인 구문을 사용하려는 경우나 추가할 태스크에 STOCK 모니커가 없는 경우에는 긴 이름을 사용하여 실행 파일에 태스크를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-141">If you prefer a more explicit syntax, or if the task that you want to add does not have a STOCK moniker, you can add the task to the executable using its long name.</span></span> <span data-ttu-id="2cd9d-142">이 구문을 사용하려면 태스크의 버전 번호도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-142">This syntax requires that you also specify the version number of the task.</span></span>  
  
```csharp  
Executable exec = package.Executables.Add(  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " +  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " +  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91");  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add( _  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " & _  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " & _  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91")  
```  
  
 <span data-ttu-id="2cd9d-143">다음 예와 같이 클래스의 **AssemblyQualifiedName** 속성을 사용하면 태스크 버전을 지정하지 않고도 프로그래밍 방식으로 태스크의 긴 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-143">You can obtain the long name for the task programmatically, without having to specify the task version, by using the **AssemblyQualifiedName** property of the class, as shown in the following example.</span></span> <span data-ttu-id="2cd9d-144">이 예에는 Microsoft.SqlServer.SQLTask 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-144">This example requires a reference to the Microsoft.SqlServer.SQLTask assembly.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask;  
...  
      Executable exec = package.Executables.Add(  
        typeof(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName);  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask  
...  
    Dim exec As Executable = package.Executables.Add( _  
      GetType(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName)  
```  
  
 <span data-ttu-id="2cd9d-145">다음 코드 예에서는 새 패키지에서 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 컬렉션을 만든 다음 `STOCK` 모니커를 사용하여 컬렉션에 .파일 시스템 태스크 및 대량 삽입 태스크를 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-145">The following code example shows how to create an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection from a new package, and then add a File System task and a Bulk Insert task to the collection, by using their `STOCK` monikers.</span></span> <span data-ttu-id="2cd9d-146">이 예에는 Microsoft.SqlServer.FileSystemTask 및 Microsoft.SqlServer.BulkInsertTask 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-146">This example requires a reference to the Microsoft.SqlServer.FileSystemTask and Microsoft.SqlServer.BulkInsertTask assemblies.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thBulkInsertTask = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        Console.WriteLine("Type {0}", taskHost.InnerObject.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thBulkInsertTask As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      Console.WriteLine("Type {0}", taskHost.InnerObject.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="2cd9d-147">**샘플 출력:**</span><span class="sxs-lookup"><span data-stu-id="2cd9d-147">**Sample Output:**</span></span>  
  
 `Type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
## <a name="taskhost-container"></a><span data-ttu-id="2cd9d-148">TaskHost 컨테이너</span><span class="sxs-lookup"><span data-stu-id="2cd9d-148">TaskHost Container</span></span>  
 <span data-ttu-id="2cd9d-149"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 클래스는 그래픽 사용자 인터페이스에는 나타나지 않는 컨테이너이지만 프로그래밍에서 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-149">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class is a container that does not appear in the graphical user interface, but is very important in programming.</span></span> <span data-ttu-id="2cd9d-150">이 클래스는 모든 태스크에 대한 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-150">This class is a wrapper for every task.</span></span> <span data-ttu-id="2cd9d-151"><xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 메서드를 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 개체로 패키지에 추가된 태스크는 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 개체로 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-151">Tasks that are added to the package by using the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object can be cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object.</span></span> <span data-ttu-id="2cd9d-152">태스크를 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>로 캐스팅하면 태스크에서 추가 속성 및 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-152">When a task is cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, you can use additional properties and methods on the task.</span></span> <span data-ttu-id="2cd9d-153">또한 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 속성을 통해 태스크 자체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-153">Also, the task itself can be accessed through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="2cd9d-154">필요에 따라 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 컬렉션을 통해 태스크의 속성을 사용할 수 있도록 태스크를 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 개체로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-154">Depending on your needs, you may decide to keep the task as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object so that you can use the properties of the task through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection.</span></span> <span data-ttu-id="2cd9d-155"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A>를 사용하면 보다 일반적인 코드를 작성할 수 있다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-155">The advantage of using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> is that you can write more generic code.</span></span> <span data-ttu-id="2cd9d-156">태스크에 대한 매우 구체적인 코드가 필요한 경우에는 태스크를 적절한 개체로 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-156">If you need very specific code for a task, then you should cast the task to its appropriate object.</span></span>  
  
 <span data-ttu-id="2cd9d-157">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>가 들어 있는 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>인 thBulkInsertTask를 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> 개체로 캐스팅하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-157">The following code example shows how to cast a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, thBulkInsertTask, that contains a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>, to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> object.</span></span>  
  
```csharp  
BulkInsertTask myTask = thBulkInsertTask.InnerObject as BulkInsertTask;  
```  
  
```vb  
Dim myTask As BulkInsertTask = CType(thBulkInsertTask.InnerObject, BulkInsertTask)  
```  
  
 <span data-ttu-id="2cd9d-158">다음 코드 예에서는 실행 파일을 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>로 캐스팅한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 속성을 사용하여 호스트에 의해 포함된 실행 파일의 유형을 확인하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-158">The following code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property to determine which type of executable is contained by the host.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask1 = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thFileSystemTask2 = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask)  
        {  
          // Do work with FileSystemTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        else if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask)  
        {  
          // Do work with BulkInsertTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        // Add additional statements to check InnerObject, if desired.  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask1 As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thFileSystemTask2 As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      If TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask Then  
        ' Do work with FileSystemTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      ElseIf TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask Then  
        ' Do work with BulkInsertTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      End If  
      ' Add additional statements to check InnerObject, if desired.  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="2cd9d-159">**샘플 출력:**</span><span class="sxs-lookup"><span data-stu-id="2cd9d-159">**Sample Output:**</span></span>  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
 <span data-ttu-id="2cd9d-160"><xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 문은 새로 만든 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 개체에서 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 개체로 캐스팅된 실행 파일을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-160">The <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> statement returns an executable that is cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object from the newly created <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object.</span></span>  
  
 <span data-ttu-id="2cd9d-161">새 개체의 속성을 설정하거나 메서드를 호출하려면 다음 두 가지 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-161">To set properties or to call methods on the new object, you have two options:</span></span>  
  
1.  <span data-ttu-id="2cd9d-162"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 컬렉션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-162">Use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="2cd9d-163">예를 들어 개체의 속성을 가져오려면 `th.Properties["propertyname"].GetValue(th))`를 사용하고,</span><span class="sxs-lookup"><span data-stu-id="2cd9d-163">For example, to obtain a property from the object, use `th.Properties["propertyname"].GetValue(th))`.</span></span> <span data-ttu-id="2cd9d-164">속성을 설정하려면 `th.Properties["propertyname"].SetValue(th, <value>);`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-164">To set a property, use `th.Properties["propertyname"].SetValue(th, <value>);`.</span></span>  
  
2.  <span data-ttu-id="2cd9d-165"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>를 태스크 클래스로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-165">Cast the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task class.</span></span> <span data-ttu-id="2cd9d-166">예를 들어 대량 삽입 태스크가 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>로 패키지에 추가된 후 이 태스크를 <xref:Microsoft.SqlServer.Dts.Runtime.Executable>로 캐스팅하고 이후에 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>로 캐스팅하려면 `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-166">For example, to cast the Bulk Insert task to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> after it has been added to a package as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> and subsequently cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, use `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`.</span></span>  
  
 <span data-ttu-id="2cd9d-167">태스크별 클래스로 캐스팅하는 대신 코드에서 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 클래스를 사용하면 다음과 같은 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-167">Using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class in code, instead of casting to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="2cd9d-168">코드에서 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 공급자가 어셈블리를 참조할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-168">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> provider does not require a reference to the assembly in the code.</span></span>  
  
-   <span data-ttu-id="2cd9d-169">컴파일 시 태스크 이름을 몰라도 되므로 모든 태스크에 대해 작동하는 일반 루틴을 코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-169">You can code generic routines that work for any task, because you do not have to know the name of the task at compile time.</span></span> <span data-ttu-id="2cd9d-170">이러한 일반 루틴에 포함된 메서드에서는 사용자가 해당 메서드에 태스크 이름을 전달하며 모든 메서드 코드가 모든 태스크에 대해 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-170">Such generic routines include methods where you pass in the name of the task to the method, and the method code works for all tasks.</span></span> <span data-ttu-id="2cd9d-171">따라서 이 메서드는 테스트 코드를 작성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-171">This is a good method for writing test code.</span></span>  
  
 <span data-ttu-id="2cd9d-172"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>에서 태스크별 클래스로 캐스팅하면 다음과 같은 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-172">Casting from the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="2cd9d-173">Visual Studio 프로젝트에서 문 완성 기능(IntelliSense)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-173">The Visual Studio project gives you statement completion (IntelliSense).</span></span>  
  
-   <span data-ttu-id="2cd9d-174">코드가 보다 빨리 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-174">The code may run faster.</span></span>  
  
-   <span data-ttu-id="2cd9d-175">태스크별 개체를 사용하면 초기 바인딩 및 결과 최적화 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-175">Task-specific objects enable early binding and the resulting optimizations.</span></span> <span data-ttu-id="2cd9d-176">초기 바인딩과 런타임 바인딩에 대한 자세한 내용은 Visual Basic 언어 개념의 "초기 바인딩 및 런타임에 바인딩" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-176">For more information about early and late binding, see the topic "Early and Late Binding" in Visual Basic Language Concepts.</span></span>  
  
 <span data-ttu-id="2cd9d-177">다음 코드 예에서는 태스크 코드 재사용의 개념을 확장하여,</span><span class="sxs-lookup"><span data-stu-id="2cd9d-177">The following code example expands on the concept of reusing task code.</span></span> <span data-ttu-id="2cd9d-178">태스크를 해당되는 특정 클래스로 캐스팅하는 대신 실행 파일을 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>로 캐스팅한 다음 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A>를 사용하여 모든 태스크에 대한 일반 코드를 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-178">Instead of casting tasks to their specific class equivalents, the code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then uses the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> to write generic code against all the tasks.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
  
      string[] tasks = { "STOCK:SQLTask", "STOCK:ScriptTask",   
        "STOCK:ExecuteProcessTask", "STOCK:PipelineTask",   
        "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask" };  
  
      foreach (string s in tasks)  
      {  
        TaskHost taskhost = package.Executables.Add(s) as TaskHost;  
        DtsProperties props = taskhost.Properties;  
        Console.WriteLine("Enumerating properties on " + taskhost.Name);  
        Console.WriteLine(" TaskHost.InnerObject is " + taskhost.InnerObject.ToString());  
        Console.WriteLine();  
  
        foreach (DtsProperty prop in props)  
        {  
          Console.WriteLine("Properties for " + prop.Name);  
          Console.WriteLine("Name : " + prop.Name);  
          Console.WriteLine("Type : " + prop.Type.ToString());  
          Console.WriteLine("Readable : " + prop.Get.ToString());  
          Console.WriteLine("Writable : " + prop.Set.ToString());  
          Console.WriteLine();  
        }  
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
  
    Dim package As Package = New Package()  
  
    Dim tasks() As String = New String() {"STOCK:SQLTask", "STOCK:ScriptTask", _  
              "STOCK:ExecuteProcessTask", "STOCK:PipelineTask", _  
              "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask"}  
  
    For Each s As String In tasks  
  
      Dim taskhost As TaskHost = CType(package.Executables.Add(s), TaskHost)  
      Dim props As DtsProperties = taskhost.Properties  
      Console.WriteLine("Enumerating properties on " & taskhost.Name)  
      Console.WriteLine(" TaskHost.InnerObject is " & taskhost.InnerObject.ToString())  
      Console.WriteLine()  
  
      For Each prop As DtsProperty In props  
        Console.WriteLine("Properties for " + prop.Name)  
        Console.WriteLine(" Name : " + prop.Name)  
        Console.WriteLine(" Type : " + prop.Type.ToString())  
        Console.WriteLine(" Readable : " + prop.Get.ToString())  
        Console.WriteLine(" Writable : " + prop.Set.ToString())  
        Console.WriteLine()  
      Next  
  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="2cd9d-179">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="2cd9d-179">External Resources</span></span>  
 <span data-ttu-id="2cd9d-180">blogs.msdn.com의 블로그 항목 - [EzAPI – SQL Server 2012용으로 업데이트됨](https://go.microsoft.com/fwlink/?LinkId=243223)</span><span class="sxs-lookup"><span data-stu-id="2cd9d-180">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="2cd9d-181">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="2cd9d-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2cd9d-182">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2cd9d-183">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2cd9d-184">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="2cd9d-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd9d-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2cd9d-185">See Also</span></span>  
 [<span data-ttu-id="2cd9d-186">프로그래밍 방식으로 태스크 연결</span><span class="sxs-lookup"><span data-stu-id="2cd9d-186">Connecting Tasks Programmatically</span></span>](../building-packages-programmatically/connecting-tasks-programmatically.md)  
  
  
