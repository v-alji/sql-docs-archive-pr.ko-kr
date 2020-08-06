---
title: CLR 통합 시작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 43c97e411a4d74aa48b88f2edbbe420ae17f3534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638838"
---
# <a name="getting-started-with-clr-integration"></a><span data-ttu-id="e6784-102">CLR 통합으로 작업 시작</span><span class="sxs-lookup"><span data-stu-id="e6784-102">Getting Started with CLR Integration</span></span>
  <span data-ttu-id="e6784-103">이 항목에서는 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] .NET FRAMEWORK CLR (공용 언어 런타임)과의 통합을 사용 하 여 데이터베이스 개체를 컴파일하는 데 필요한 네임 스페이스 및 라이브러리에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-103">This topic provides an overview of the namespaces and libraries required to compile database objects using the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="e6784-104">또한 이 항목에서는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#으로 작성된 간단한 CLR 저장 프로시저를 작성, 컴파일 및 실행하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-104">The topic also shows you how to write, compile, and run a simple CLR stored procedure written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
## <a name="required-namespaces"></a><span data-ttu-id="e6784-105">필수 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="e6784-105">Required Namespaces</span></span>  
 <span data-ttu-id="e6784-106">부터 시작 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-106">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e6784-107">CLR 통합 기능은 .NET Framework의 일부인 system.data.dll이라는 어셈블리에서 제공되며</span><span class="sxs-lookup"><span data-stu-id="e6784-107">CLR integration functionality is exposed in an assembly called system.data.dll, which is part of the .NET Framework.</span></span> <span data-ttu-id="e6784-108">이 어셈블리는 GAC(전역 어셈블리 캐시)와 .NET Framework 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-108">This assembly can be found in the Global Assembly Cache (GAC) as well as in the .NET Framework directory.</span></span> <span data-ttu-id="e6784-109">이 어셈블리에 대한 참조는 일반적으로 명령줄 도구와 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio에 자동으로 추가되므로 직접 추가하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-109">A reference to this assembly is typically added automatically by both command line tools and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, so there is no need to add it manually.</span></span>  
  
 <span data-ttu-id="e6784-110">system.data.dll 어셈블리에는 CLR 데이터베이스 개체를 컴파일하는 데 필요한 다음과 같은 네임스페이스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-110">The system.data.dll assembly contains the following namespaces, which are required for compiling CLR database objects:</span></span>  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a><span data-ttu-id="e6784-111">간단한 "Hello World" 저장 프로시저 작성</span><span class="sxs-lookup"><span data-stu-id="e6784-111">Writing A Simple "Hello World" Stored Procedure</span></span>  
 <span data-ttu-id="e6784-112">아래의 Visual C# 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 코드를 복사하여 텍스트 편집기에 붙여넣고 이름이 "helloworld.cs" 또는 "helloworld.vb"인 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-112">Copy and paste the following Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic code into a text editor, and save it in a file named "helloworld.cs" or "helloworld.vb".</span></span>  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="e6784-113">이 간단한 프로그램에는 공용 클래스에 대한 정적 메서드 하나가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-113">This simple program contains a single static method on a public class.</span></span> <span data-ttu-id="e6784-114">이 메서드는 간단한 텍스트 메시지를 출력할 관리되는 데이터베이스 개체를 만들기 위해 `SqlContext`와 `SqlPipe`라는 새로운 클래스 두 개를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-114">This method uses two new classes, `SqlContext` and `SqlPipe`, for creating managed database objects to output a simple text message.</span></span> <span data-ttu-id="e6784-115">또한 이 메서드는 "Hello world!"라는 문자열을</span><span class="sxs-lookup"><span data-stu-id="e6784-115">The method also assigns the string "Hello world!"</span></span> <span data-ttu-id="e6784-116">out 매개 변수 값으로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-116">as the value of an out parameter.</span></span> <span data-ttu-id="e6784-117">저장 프로시저에서이 메서드를 저장 프로시저로 선언할 수 있습니다 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e6784-117">This method can be declared as a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] stored procedure.</span></span>  
  
 <span data-ttu-id="e6784-118">이제 이 프로그램을 라이브러리로 컴파일하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로드한 다음 저장 프로시저로 실행해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-118">We will now compile this program as a library, load it into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and run it as a stored procedure.</span></span>  
  
## <a name="compiling-the-hello-world-stored-procedure"></a><span data-ttu-id="e6784-119">"Hello World" 저장 프로시저 컴파일</span><span class="sxs-lookup"><span data-stu-id="e6784-119">Compiling the "Hello World" Stored Procedure</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)]<span data-ttu-id="e6784-120">기본적으로 재배포 파일을 .NET Framework 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-120">.NET Framework redistribution files by default.</span></span> <span data-ttu-id="e6784-121">이러한 파일에는 csc.exe와 vbc.exe, 그리고 Visual C# 및 Visual Basic 프로그램용 명령줄 컴파일러가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-121">These files include csc.exe and vbc.exe, the command-line compilers for Visual C# and Visual Basic programs.</span></span> <span data-ttu-id="e6784-122">예제를 컴파일하려면 csc.exe 또는 vbc.exe가 포함된 디렉터리를 가리키도록 경로 변수를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-122">In order to compile our sample, you must modify your path variable to point to the directory containing csc.exe or vbc.exe.</span></span> <span data-ttu-id="e6784-123">.NET Framework의 기본 설치 경로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-123">The following is the default installation path of the .NET Framework.</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 <span data-ttu-id="e6784-124">version에는 설치된 .NET Framework 재배포 가능 패키지의 버전 번호가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-124">Version contains the version number of the installed .NET Framework redistributable.</span></span> <span data-ttu-id="e6784-125">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-125">For example:</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 <span data-ttu-id="e6784-126">경로에 .NET Framework 디렉터리를 추가한 후에는 다음 명령을 사용하여 예제 저장 프로시저를 어셈블리로 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-126">Once you have added the .NET Framework directory to your path, you can compile the sample stored procedure into an assembly with the following command.</span></span> <span data-ttu-id="e6784-127">`/target` 옵션을 사용하면 저장 프로시저를 어셈블리로 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-127">The `/target` option allows you to compile it into an assembly.</span></span>  
  
 <span data-ttu-id="e6784-128">Visual C# 원본 파일의 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-128">For Visual C# source files:</span></span>  
  
```  
csc /target:library helloworld.cs   
```  
  
 <span data-ttu-id="e6784-129">Visual Basic 원본 파일의 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-129">For Visual Basic source files:</span></span>  
  
```  
vbc /target:library helloworld.vb  
```  
  
 <span data-ttu-id="e6784-130">이러한 명령은 라이브러리 DLL을 빌드하도록 지정하는 /target 옵션을 사용하여 Visual C# 또는 Visual Basic 컴파일러를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-130">These commands launch the Visual C# or Visual Basic compiler using the /target option to specify building a library DLL.</span></span>  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a><span data-ttu-id="e6784-131">SQL Server에서 "Hello World" 저장 프로시저 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="e6784-131">Loading and Running the "Hello World" Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="e6784-132">샘플 프로시저가 성공적으로 컴파일되면에서 테스트 하 [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] 고 새 쿼리를 만들어 적절 한 테스트 데이터베이스 (예: AdventureWorks 예제 데이터베이스)에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-132">Once the sample procedure has successfully compiled, you can test it in [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] and create a new query, connecting to a suitable test database (for example, the AdventureWorks sample database).</span></span>  
  
 <span data-ttu-id="e6784-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 CLR(공용 언어 런타임) 코드를 실행하는 기능이 기본적으로 OFF로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-133">The ability to execute common language runtime (CLR) code is set to OFF by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e6784-134">**Sp_configure** 시스템 저장 프로시저를 사용 하 여 CLR 코드를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-134">The CLR code can be enabled by using the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="e6784-135">자세한 내용은 [Enabling CLR Integration](../clr-integration-enabling.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6784-135">For more information, see [Enabling CLR Integration](../clr-integration-enabling.md).</span></span>  
  
 <span data-ttu-id="e6784-136">저장 프로시저에 액세스할 수 있게 어셈블리를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-136">We will need to create the assembly so we can access the stored procedure.</span></span> <span data-ttu-id="e6784-137">이 예에서는 C:\ 디렉터리에 helloworld.dll 어셈블리를 만들었다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-137">For this example, we will assume that you have created the helloworld.dll assembly in the C:\ directory.</span></span> <span data-ttu-id="e6784-138">쿼리에 다음의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-138">Add the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to your query.</span></span>  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 <span data-ttu-id="e6784-139">어셈블리가 만들어지면 CREATE PROCEDURE 문을 사용하여 HelloWorld 메서드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-139">Once the assembly has been created, we can now access our HelloWorld method by using the create procedure statement.</span></span> <span data-ttu-id="e6784-140">여기서 저장 프로시저 이름은 "hello"입니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-140">We will call our stored procedure "hello":</span></span>  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 <span data-ttu-id="e6784-141">프로시저가 만들어지면 [!INCLUDE[tsql](../../../includes/tsql-md.md)]로 작성된 일반적인 저장 프로시저와 마찬가지로 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-141">Once the procedure has been created, it can be run just like a normal stored procedure written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e6784-142">다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-142">Execute the following command:</span></span>  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 <span data-ttu-id="e6784-143">그러면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 메시지 창에 다음과 같은 메시지가 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-143">This should result in the following output in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] messages window.</span></span>  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a><span data-ttu-id="e6784-144">"Hello World" 저장 프로시저 예제 제거</span><span class="sxs-lookup"><span data-stu-id="e6784-144">Removing the "Hello World" Stored Procedure Sample</span></span>  
 <span data-ttu-id="e6784-145">예제 저장 프로시저 실행이 완료되면 프로시저와 어셈블리를 테스트 데이터베이스에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-145">When you are finished running the sample stored procedure, you can remove the procedure and the assembly from your test database.</span></span>  
  
 <span data-ttu-id="e6784-146">먼저 drop procedure 명령을 사용하여 프로시저를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-146">First, remove the procedure using the drop procedure command.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 <span data-ttu-id="e6784-147">프로시저가 삭제되면 예제 코드가 포함된 어셈블리를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6784-147">Once the procedure has been dropped, you can remove the assembly containing your sample code.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6784-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6784-148">See Also</span></span>  
 <span data-ttu-id="e6784-149">[CLR 저장 프로시저](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e6784-149">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 <span data-ttu-id="e6784-150">[ADO.NET에 대 한 In-process 특정 확장 SQL Server](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span><span class="sxs-lookup"><span data-stu-id="e6784-150">[SQL Server In-Process Specific Extensions to ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span></span>  
 <span data-ttu-id="e6784-151">[CLR 데이터베이스 개체 디버깅](../debugging-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="e6784-151">[Debugging CLR Database Objects](../debugging-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="e6784-152">CLR 통합 보안</span><span class="sxs-lookup"><span data-stu-id="e6784-152">CLR Integration Security</span></span>](../security/clr-integration-security.md)  
  
  
