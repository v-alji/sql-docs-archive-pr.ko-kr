---
title: 사용자 지정 태스크 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f752acad7a442a8e0aad2d24e94938c14195a35d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652217"
---
# <a name="creating-a-custom-task"></a><span data-ttu-id="b576d-102">사용자 지정 태스크 만들기</span><span class="sxs-lookup"><span data-stu-id="b576d-102">Creating a Custom Task</span></span>
  <span data-ttu-id="b576d-103">사용자 지정 태스크를 만드는 단계는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]의 다른 사용자 지정 개체를 만드는 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-103">The steps involved in creating a custom task are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b576d-104">기본 클래스에서 상속되는 새 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="b576d-105">태스크의 경우 기본 클래스는 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task)입니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-105">For a task, the base class is [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task).</span></span>  
  
-   <span data-ttu-id="b576d-106">개체 유형을 식별하는 특성을 클래스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="b576d-107">태스크의 경우 이 특성은 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>입니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-107">For a task, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.</span></span>  
  
-   <span data-ttu-id="b576d-108">기본 클래스의 메서드 및 속성 구현을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="b576d-109">태스크의 경우 이러한 메서드로는 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-109">For a task, these include the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
-   <span data-ttu-id="b576d-110">필요한 경우 사용자 지정 사용자 인터페이스를 개발합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="b576d-111">태스크의 경우 사용자 지정 사용자 인터페이스를 개발하려면 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 인터페이스를 구현하는 클래스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-111">For a task, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface.</span></span>  
  
## <a name="getting-started-with-a-custom-task"></a><span data-ttu-id="b576d-112">사용자 지정 태스크 시작</span><span class="sxs-lookup"><span data-stu-id="b576d-112">Getting Started with a Custom Task</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="b576d-113">프로젝트 및 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b576d-113">Creating Projects and Classes</span></span>  
 <span data-ttu-id="b576d-114">관리되는 태스크는 모두 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 기본 클래스에서 파생되므로 사용자 지정 태스크를 만들려면 먼저 관리되는 프로그래밍 언어로 클래스 라이브러리 프로젝트를 만들고 기본 클래스에서 상속되는 클래스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-114">Because all managed tasks derive from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, the first step when you create a custom task is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="b576d-115">이 파생 클래스에서 기본 클래스의 메서드 및 속성을 재정의하여 사용자 지정 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-115">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="b576d-116">동일한 솔루션에서 사용자 지정 사용자 인터페이스에 대한 두 번째 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-116">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="b576d-117">배포를 쉽게 하려면 사용자 인터페이스에 대한 별도의 어셈블리를 만드는 것이 좋습니다. 이렇게 하면 연결 관리자 또는 해당 사용자 인터페이스를 독립적으로 업데이트하거나 다시 배포할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-117">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="b576d-118">강력한 이름 키 파일을 사용하여 빌드 시 생성될 어셈블리에 서명하도록 두 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-118">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtstask-attribute"></a><span data-ttu-id="b576d-119">DtsTask 특성 적용</span><span class="sxs-lookup"><span data-stu-id="b576d-119">Applying the DtsTask Attribute</span></span>  
 <span data-ttu-id="b576d-120">앞에서 만든 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 특성을 적용하여 해당 클래스를 태스크로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-120">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class that you have created to identify it as a task.</span></span> <span data-ttu-id="b576d-121">이 특성은 태스크의 이름, 설명 및 태스크 유형 같은 디자인 타임 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-121">This attribute provides design-time information such as the name, description, and task type of the task.</span></span>  
  
 <span data-ttu-id="b576d-122"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 속성을 사용하여 태스크를 사용자 지정 사용자 인터페이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property to link the task to its custom user interface.</span></span> <span data-ttu-id="b576d-123">이 속성에 필요한 공개 키 토큰을 가져오려면 **sn.exe -t**를 사용하여 사용자 인터페이스 어셈블리 서명에 사용할 키 쌍(.snk) 파일의 공개 키 토큰을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-123">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
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
  
## <a name="building-deploying-and-debugging-a-custom-task"></a><span data-ttu-id="b576d-124">사용자 지정 태스크 빌드, 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="b576d-124">Building, Deploying, and Debugging a Custom Task</span></span>  
 <span data-ttu-id="b576d-125">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 사용자 지정 태스크의 빌드, 배포 및 디버깅 단계는 다른 형식의 사용자 지정 개체에 대해 필요한 단계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b576d-125">The steps for building, deploying, and debugging a custom task in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="b576d-126">자세한 내용은 [사용자 지정 개체 빌드, 배포 및 디버그](../building-deploying-and-debugging-custom-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b576d-126">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="b576d-127">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="b576d-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b576d-128">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="b576d-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b576d-129">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="b576d-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b576d-130">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="b576d-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b576d-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b576d-131">See Also</span></span>  
 <span data-ttu-id="b576d-132">[사용자 지정 태스크 만들기](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="b576d-132">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="b576d-133">[사용자 지정 태스크 코딩](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="b576d-133">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="b576d-134">사용자 지정 태스크의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="b576d-134">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
