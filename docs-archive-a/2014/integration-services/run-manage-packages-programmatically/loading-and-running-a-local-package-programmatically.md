---
title: 프로그래밍 방식으로 로컬 패키지 로드 및 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a29faf623c02fea4fd8722c235f595f0fe4492e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729555"
---
# <a name="loading-and-running-a-local-package-programmatically"></a><span data-ttu-id="cb582-102">프로그래밍 방식으로 로컬 패키지 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="cb582-102">Loading and Running a Local Package Programmatically</span></span>
  <span data-ttu-id="cb582-103">[패키지 실행](../packages/run-integration-services-ssis-packages.md)에 설명된 방법을 사용하여 필요에 따라 또는 미리 지정한 시간에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-103">You can run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages as needed or at predetermined times by using the methods described in [Running Packages](../packages/run-integration-services-ssis-packages.md).</span></span> <span data-ttu-id="cb582-104">그러나 단 몇 줄의 코드로도 Windows Forms 애플리케이션, 콘솔 애플리케이션, ASP.NET Web Form 또는 웹 서비스, Windows 서비스 등의 사용자 지정 애플리케이션에서 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-104">However, with only a few lines of code, you can also run a package from a custom application such as a Windows Forms application, a console application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
 <span data-ttu-id="cb582-105">이 항목에서는 다음과 같은 주제를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-105">This topic discusses:</span></span>  
  
-   <span data-ttu-id="cb582-106">프로그래밍 방식으로 패키지 로드</span><span class="sxs-lookup"><span data-stu-id="cb582-106">Loading a package programmatically</span></span>  
  
-   <span data-ttu-id="cb582-107">프로그래밍 방식으로 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="cb582-107">Running a package programmatically</span></span>  
  
 <span data-ttu-id="cb582-108">이 항목에서 설명하는 패키지 로드 및 실행 방법을 사용할 경우에는 항상 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-108">All of the methods used in this topic to load and run packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="cb582-109">새 프로젝트에 참조를 추가한 후에는 `using` 또는 `Imports` 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-109">After adding the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="loading-a-package-programmatically"></a><span data-ttu-id="cb582-110">프로그래밍 방식으로 패키지 로드</span><span class="sxs-lookup"><span data-stu-id="cb582-110">Loading a Package Programmatically</span></span>  
 <span data-ttu-id="cb582-111">로컬 컴퓨터에서 프로그래밍 방식으로 패키지를 로드하려면 패키지가 로컬 위치에 저장되어 있든 원격 위치에 저장되어 있든 관계없이 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-111">To load a package programmatically on the local computer, whether the package is stored locally or remotely, call one of the following methods:</span></span>  
  
|<span data-ttu-id="cb582-112">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="cb582-112">Storage Location</span></span>|<span data-ttu-id="cb582-113">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="cb582-113">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="cb582-114">파일</span><span class="sxs-lookup"><span data-stu-id="cb582-114">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|<span data-ttu-id="cb582-115">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="cb582-115">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cb582-116">SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 ".", localhost 또는 로컬 서버의 서버 이름만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-116">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="cb582-117">"(local)"은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-117">You cannot use "(local)".</span></span>  
  
## <a name="running-a-package-programmatically"></a><span data-ttu-id="cb582-118">프로그래밍 방식으로 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="cb582-118">Running a Package Programmatically</span></span>  
 <span data-ttu-id="cb582-119">로컬 컴퓨터에서 패키지를 실행하는 관리 코드로 사용자 지정 애플리케이션을 개발하려면 다음 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-119">Developing a custom application in managed code that runs a package on the local computer requires the following approach.</span></span> <span data-ttu-id="cb582-120">여기에 요약된 단계는 뒷부분의 예제 콘솔 애플리케이션에서 자세히 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-120">The steps summarized here are demonstrated in the sample console application that follows.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a><span data-ttu-id="cb582-121">로컬 컴퓨터에서 프로그래밍 방식으로 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="cb582-121">To run a package on the local computer programmatically</span></span>  
  
1.  <span data-ttu-id="cb582-122">Visual Studio 개발 환경을 시작하고 원하는 개발 언어로 새 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-122">Start the Visual Studio development environment, and create a new application in your preferred development language.</span></span> <span data-ttu-id="cb582-123">이 예에서는 콘솔 애플리케이션을 사용하지만 Windows Forms 애플리케이션, ASP.NET Web Form 또는 Web 서비스, Windows 서비스 등에서 패키지를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-123">This example uses a console application; however you can also run a package from a Windows Forms application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
2.  <span data-ttu-id="cb582-124">**프로젝트** 메뉴에서 **참조 추가**를 클릭하고 **Microsoft.SqlServer.ManagedDTS.dll**에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-124">On the **Project** menu, click **Add Reference** and add a reference to **Microsoft.SqlServer.ManagedDTS.dll**.</span></span> <span data-ttu-id="cb582-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-125">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="cb582-126">Visual Basic `Imports` 문 또는 c # 문을 사용 `using` 하 여 **Microsoft sql server Runtime** 네임 스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-126">Use the Visual Basic `Imports` statement or the C# `using` statement to import the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
4.  <span data-ttu-id="cb582-127">기본 루틴에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-127">Add the following code in the main routine.</span></span> <span data-ttu-id="cb582-128">완성된 콘솔 애플리케이션은 다음 예와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-128">The completed console application should look like the following example.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb582-129">예제 코드에서는 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> 메서드를 사용하여 파일 시스템에서 패키지를 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-129">The sample code demonstrates loading the package from the file system by using the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> method.</span></span> <span data-ttu-id="cb582-130">그러나 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> 메서드를 호출하여 MSDB 데이터베이스에서 패키지를 로드하거나 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 메서드를 호출하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 저장소에서 패키지를 로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-130">However you can also load the package from the MSDB database by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> method, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> method.</span></span>  
  
5.  <span data-ttu-id="cb582-131">프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-131">Run the project.</span></span> <span data-ttu-id="cb582-132">예제 코드에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 예제와 함께 설치된 CalculatedColumns 예제 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-132">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="cb582-133">패키지 실행 결과는 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-133">The result of package execution is displayed in the console window.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="cb582-134">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="cb582-134">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a><span data-ttu-id="cb582-135">실행 중인 패키지에서 이벤트 캡처</span><span class="sxs-lookup"><span data-stu-id="cb582-135">Capturing Events from a Running Package</span></span>  
 <span data-ttu-id="cb582-136">위의 예제에 표시된 대로 패키지를 프로그래밍 방식으로 실행할 경우 패키지를 실행할 때 발생하는 오류와 기타 이벤트를 캡처할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-136">When you run a package programmatically as shown in the preceding sample, you may also want to capture errors and other events that occur as the package executes.</span></span> <span data-ttu-id="cb582-137"><xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 클래스에서 상속되는 클래스를 추가하고 패키지를 로드할 때 해당 클래스에 대한 참조를 전달하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-137">You can accomplish this by adding a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class, and by passing a reference to that class when you load the package.</span></span> <span data-ttu-id="cb582-138">다음 예에서는 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> 이벤트만 캡처하지만 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 클래스에서 캡처할 수 있는 다른 이벤트도 여러 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-138">Although the following example captures only the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> event, there are many other events that the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class lets you capture.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a><span data-ttu-id="cb582-139">로컬 컴퓨터에서 프로그래밍 방식으로 패키지를 실행하고 패키지 이벤트를 캡처하려면</span><span class="sxs-lookup"><span data-stu-id="cb582-139">To run a package on the local computer programmatically and capture package events</span></span>  
  
1.  <span data-ttu-id="cb582-140">위 예의 단계에 따라 이 예에서 사용할 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-140">Follow the steps in the preceding example to create a project for this example.</span></span>  
  
2.  <span data-ttu-id="cb582-141">기본 루틴에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-141">Add the following code in the main routine.</span></span> <span data-ttu-id="cb582-142">완성된 콘솔 애플리케이션은 다음 예와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-142">The completed console application should look like the following example.</span></span>  
  
3.  <span data-ttu-id="cb582-143">프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-143">Run the project.</span></span> <span data-ttu-id="cb582-144">예제 코드에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 예제와 함께 설치된 CalculatedColumns 예제 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-144">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="cb582-145">패키지 실행 결과는 발생한 오류와 함께 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb582-145">The result of package execution is displayed in the console window, along with any errors that occur.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="cb582-146">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="cb582-146">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application-specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
<span data-ttu-id="cb582-147">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="cb582-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cb582-148">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cb582-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cb582-149">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="cb582-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cb582-150">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="cb582-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb582-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb582-151">See Also</span></span>  
 <span data-ttu-id="cb582-152">[로컬 실행과 원격 실행의 차이점 이해](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="cb582-152">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="cb582-153">[프로그래밍 방식으로 원격 패키지 로드 및 실행](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="cb582-153">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="cb582-154">로컬 패키지의 출력 로드</span><span class="sxs-lookup"><span data-stu-id="cb582-154">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
