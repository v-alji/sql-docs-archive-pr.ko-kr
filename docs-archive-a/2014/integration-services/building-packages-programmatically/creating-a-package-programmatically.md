---
title: 프로그래밍 방식으로 패키지 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1159784fc95dd86d9d33c4354291cc7c52812982
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731975"
---
# <a name="creating-a-package-programmatically"></a><span data-ttu-id="e4dbf-102">프로그래밍 방식으로 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="e4dbf-102">Creating a Package Programmatically</span></span>
  <span data-ttu-id="e4dbf-103"><xref:Microsoft.SqlServer.Dts.Runtime.Package> 개체는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 프로젝트 솔루션에 있는 다른 모든 개체의 최상위 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-103">The <xref:Microsoft.SqlServer.Dts.Runtime.Package> object is the top-level container for all other objects in an [!INCLUDE[ssIS](../../includes/ssis-md.md)] project solution.</span></span> <span data-ttu-id="e4dbf-104">최상위 컨테이너인 패키지는 첫 번째로 만들어지는 개체이며 그 이후에 만들어지는 개체는 패키지에 추가된 다음 패키지의 컨텍스트 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-104">As the top-level container, the package is the first object created, and subsequent objects are added to it, and then executed within the context of the package.</span></span> <span data-ttu-id="e4dbf-105">패키지 자체는 데이터를 이동하거나 변환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-105">The package itself does not move or transform data.</span></span> <span data-ttu-id="e4dbf-106">패키지는 패키지에 포함된 태스크를 통해서만 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-106">The package relies on the tasks it contains to perform the work.</span></span> <span data-ttu-id="e4dbf-107">태스크는 패키지에서 수행하는 대부분의 작업을 수행하고 패키지의 기능을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-107">Tasks perform most of the work performed by a package, and define the functionality of a package.</span></span> <span data-ttu-id="e4dbf-108">단 세 줄의 코드만으로도 패키지를 만들고 실행할 수 있지만 다양한 태스크와 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체를 추가하면 패키지에 추가 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-108">A package is created and executed with just three lines of code, but various tasks and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects are added to give additional functionality to your package.</span></span> <span data-ttu-id="e4dbf-109">이 섹션에서는 프로그래밍 방식으로 패키지를 만드는 방법을 설명하며,</span><span class="sxs-lookup"><span data-stu-id="e4dbf-109">This section discusses how to programmatically create a package.</span></span> <span data-ttu-id="e4dbf-110">태스크 또는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>를 만드는 방법에 대해서는 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-110">It does not provide information about how to create the tasks or the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span> <span data-ttu-id="e4dbf-111">이러한 내용은 뒷부분의 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-111">These are covered in later sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4dbf-112">예제</span><span class="sxs-lookup"><span data-stu-id="e4dbf-112">Example</span></span>  
 <span data-ttu-id="e4dbf-113">Visual Studio IDE를 사용하여 코드를 작성하려면 Microsoft.SqlServer.Dts.Runtime에 `using` 문(Visual Basic .NET의 경우 `Imports`)을 만들기 위한 Microsoft.SqlServer.ManagedDTS.DLL에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-113">To write code using the Visual Studio IDE, a reference to Microsoft.SqlServer.ManagedDTS.DLL is required in order to create a `using` statement (`Imports` in Visual Basic .NET) to the Microsoft.SqlServer.Dts.Runtime.</span></span> <span data-ttu-id="e4dbf-114">다음 코드 예제에서는 빈 패키지를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-114">The following code sample demonstrates creating an empty package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="e4dbf-115">예제를 컴파일하고 실행하려면 Visual Studio에서 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-115">To compile and run the sample, press F5 in Visual Studio.</span></span> <span data-ttu-id="e4dbf-116">C# 컴파일러인 **csc.exe**를 사용하여 코드를 빌드하려면 명령 프롬프트에서 다음 명령과 파일 참조를 사용하여 코드를 컴파일합니다. 이때 *\<filename>* 은 .cs 또는 .vb 파일의 이름으로 바꾸고 원하는 *\<outputfilename>* 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-116">To build the code using the C# compiler, **csc.exe**, at the command prompt to compile, use the following command and file references, replacing the *\<filename>* with the name of the .cs or .vb file, and giving it an *\<outputfilename>* of your choice.</span></span>  
  
 <span data-ttu-id="e4dbf-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span><span class="sxs-lookup"><span data-stu-id="e4dbf-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="e4dbf-118">Visual Basic .NET 컴파일러인 **vbc.exe**를 사용하여 코드를 빌드하려면 명령 프롬프트에서 다음 명령과 파일 참조를 사용하여 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-118">To build the code using the Visual Basic .NET compiler, **vbc.exe**, at the command prompt to compile, use the following command and file references.</span></span>  
  
 <span data-ttu-id="e4dbf-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span><span class="sxs-lookup"><span data-stu-id="e4dbf-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="e4dbf-120">디스크에 저장된 기존 패키지를 파일 시스템이나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 로드하여 패키지를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-120">You can also create a package by loading an existing package that was saved on disk, in the file system, or to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e4dbf-121">이때 차이점은 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 개체가 먼저 만들어진 다음 패키지 개체가 애플리케이션의 오버로드된 메서드인 `LoadPackage`(플랫 파일의 경우), `LoadFromSQLServer`([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장된 패키지의 경우) 또는 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>(파일 시스템에 저장된 패키지의 경우) 중 하나로 채워진다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-121">The difference is that the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object is first created, and then the package object is filled by one of the Application's overloaded methods: `LoadPackage` for flat files, `LoadFromSQLServer` for packages saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> for packages saved to the file system.</span></span> <span data-ttu-id="e4dbf-122">다음 예에서는 디스크에서 기존 패키지를 로드한 다음 패키지의 여러 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-122">The following example loads an existing package from disk, and then views several properties on the package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="e4dbf-123">**샘플 출력:**</span><span class="sxs-lookup"><span data-stu-id="e4dbf-123">**Sample Output:**</span></span>  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a><span data-ttu-id="e4dbf-124">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="e4dbf-124">External Resources</span></span>  
  
-   <span data-ttu-id="e4dbf-125">blogs.msdn.com의 블로그 항목 - [API 예제 - OleDB 원본 및 OleDB 대상](https://go.microsoft.com/fwlink/?LinkId=220824)</span><span class="sxs-lookup"><span data-stu-id="e4dbf-125">Blog entry, [API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824), on blogs.msdn.com.</span></span>  
  
-   <span data-ttu-id="e4dbf-126">blogs.msdn.com의 블로그 항목 - [EzAPI – SQL Server 2012용으로 업데이트됨](https://go.microsoft.com/fwlink/?LinkId=243223)</span><span class="sxs-lookup"><span data-stu-id="e4dbf-126">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="e4dbf-127">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e4dbf-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e4dbf-128">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e4dbf-129">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e4dbf-130">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="e4dbf-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4dbf-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4dbf-131">See Also</span></span>  
 [<span data-ttu-id="e4dbf-132">프로그래밍 방식으로 태스크 추가</span><span class="sxs-lookup"><span data-stu-id="e4dbf-132">Adding Tasks Programmatically</span></span>](../building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
