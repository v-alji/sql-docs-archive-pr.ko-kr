---
title: 프로그래밍 방식으로 원격 패키지 로드 및 실행 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- remote packages [Integration Services]
ms.assetid: 9f6ef376-3408-46bf-b5fa-fc7b18c689c9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06565140ae8ea3603461e2944e242aa91213de47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740155"
---
# <a name="loading-and-running-a-remote-package-programmatically"></a><span data-ttu-id="46dfb-102">프로그래밍 방식으로 원격 패키지 로드 및 실행</span><span class="sxs-lookup"><span data-stu-id="46dfb-102">Loading and Running a Remote Package Programmatically</span></span>
  <span data-ttu-id="46dfb-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]가 설치되어 있지 않은 로컬 컴퓨터에서 원격 패키지를 실행하려면 패키지를 시작할 때 해당 패키지가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]가 설치된 원격 컴퓨터에서 실행되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-103">To run remote packages from a local computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, start the packages so that they run on the remote computer on which [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span> <span data-ttu-id="46dfb-104">이렇게 하려면 로컬 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트, 웹 서비스 또는 원격 구성 요소를 사용하여 원격 컴퓨터에서 패키지를 시작하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-104">You do this by having the local computer use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, a Web service, or a remote component to start the packages on the remote computer.</span></span> <span data-ttu-id="46dfb-105">로컬 컴퓨터에서 직접 원격 패키지를 시작하면 패키지가 로컬 컴퓨터로 로드되어 로컬 컴퓨터에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-105">If you try to start the remote packages directly from the local computer, the packages will load onto and try to run from the local computer.</span></span> <span data-ttu-id="46dfb-106">로컬 컴퓨터에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]가 설치되어 있지 않으면 패키지가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-106">If the local computer does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, the packages will not run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46dfb-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]가 설치되지 않은 클라이언트 컴퓨터의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 외부에서는 패키지를 실행할 수 없으며, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용권 계약에 따라 추가 컴퓨터에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]를 설치하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-107">You cannot run packages outside [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing might not let you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="46dfb-108">는 서버 구성 요소이며 클라이언트 컴퓨터에 재배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-108">is a server component and is not redistributable to client computers.</span></span>  
  
 <span data-ttu-id="46dfb-109">또는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]가 설치된 로컬 컴퓨터에서 원격 패키지를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-109">Alternately, you can run a remote package from a local computer that has [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed.</span></span> <span data-ttu-id="46dfb-110">자세한 내용은 [프로그래밍 방식으로 로컬 패키지 로드 및 실행](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46dfb-110">For more information, see [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md).</span></span>  
  
##  <a name="running-a-remote-package-on-the-remote-computer"></a><a name="top"></a> <span data-ttu-id="46dfb-111">원격 컴퓨터에서 원격 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="46dfb-111">Running a Remote Package on the Remote Computer</span></span>  
 <span data-ttu-id="46dfb-112">위에서 언급한 대로 원격 서버에서 원격 패키지를 실행하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-112">As mentioned above, there are multiple ways in which you can run a remote package on a remote server:</span></span>  
  
-   [<span data-ttu-id="46dfb-113">SQL Server 에이전트를 사용하여 프로그래밍 방식으로 원격 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="46dfb-113">Use SQL Server Agent to run the remote package programmatically</span></span>](#agent)  
  
-   [<span data-ttu-id="46dfb-114">웹 서비스 또는 원격 구성 요소를 사용하여 프로그래밍 방식으로 원격 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="46dfb-114">Use a Web service or remote component to run the remote package programmatically</span></span>](#service)  
  
 <span data-ttu-id="46dfb-115">이 항목에서 설명하는 패키지 로드 및 저장 방법을 사용할 경우에는 대부분 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-115">Almost all the methods that are used in this topic to load and save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="46dfb-116">예외는 **sp_start_job** 저장 프로시저를 실행 하기 위해이 항목에서 설명 하는 ADO.NET 방법입니다 .이 방법에서는에 대 한 참조만 필요 합니다 `System.Data` .</span><span class="sxs-lookup"><span data-stu-id="46dfb-116">The exception is the ADO.NET approach demonstrated in this topic for executing the **sp_start_job** stored procedure, which requires only a reference to `System.Data`.</span></span> <span data-ttu-id="46dfb-117">새 프로젝트에 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조를 추가한 후에는 `using` 또는 `Imports` 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-117">After you add the reference to the `Microsoft.SqlServer.ManagedDTS` assembly in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
###  <a name="using-sql-server-agent-to-run-a-remote-package-programmatically-on-the-server"></a><a name="agent"></a> <span data-ttu-id="46dfb-118">SQL Server 에이전트를 사용하여 서버에서 프로그래밍 방식으로 원격 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="46dfb-118">Using SQL Server Agent to Run a Remote Package Programmatically on the Server</span></span>  
 <span data-ttu-id="46dfb-119">다음 코드 예제에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 프로그래밍 방식으로 사용하여 서버에서 원격 패키지를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-119">The following code sample demonstrates how to programmatically use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a remote package on the server.</span></span> <span data-ttu-id="46dfb-120">이 코드 샘플에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 시작하는 **sp_start_job** 시스템 저장 프로시저를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-120">The code sample calls the system stored procedure, **sp_start_job**, which launches a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="46dfb-121">이 프로시저가 시작하는 작업의 이름은 `RunSSISPackage`이며 이 작업은 원격 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-121">The job that the procedure launches is named `RunSSISPackage`, and this job is on the remote computer.</span></span> <span data-ttu-id="46dfb-122">그런 다음 `RunSSISPackage` 작업은 원격 컴퓨터에서 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-122">The `RunSSISPackage` job then runs the package on the remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46dfb-123">**sp_start_job** 저장 프로시저의 반환 값은 저장 프로시저에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 성공적으로 시작할 수 있었는지 여부를 나타내며,</span><span class="sxs-lookup"><span data-stu-id="46dfb-123">The return value of the **sp_start_job** stored procedure indicates whether the stored procedure was able to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job successfully.</span></span> <span data-ttu-id="46dfb-124">패키지가 성공했는지 실패했는지를 나타내지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-124">The return value does not indicate whether the package succeeded or failed.</span></span>  
  
 <span data-ttu-id="46dfb-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에서 실행되는 패키지 문제를 해결하는 방법에 대한 자세한 내용은 [SSIS 패키지는 SQL Server 에이전트 작업 단계에서 호출 될 때 실행되지 않습니다.](https://support.microsoft.com/kb/918760) Microsoft 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46dfb-125">For information on troubleshooting packages that are run from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, see the Microsoft article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760).</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="46dfb-126">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="46dfb-126">Sample Code</span></span>  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
  
    Dim jobConnection As SqlConnection  
    Dim jobCommand As SqlCommand  
    Dim jobReturnValue As SqlParameter  
    Dim jobParameter As SqlParameter  
    Dim jobResult As Integer  
  
    jobConnection = New SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI")  
    jobCommand = New SqlCommand("sp_start_job", jobConnection)  
    jobCommand.CommandType = CommandType.StoredProcedure  
  
    jobReturnValue = New SqlParameter("@RETURN_VALUE", SqlDbType.Int)  
    jobReturnValue.Direction = ParameterDirection.ReturnValue  
    jobCommand.Parameters.Add(jobReturnValue)  
  
    jobParameter = New SqlParameter("@job_name", SqlDbType.VarChar)  
    jobParameter.Direction = ParameterDirection.Input  
    jobCommand.Parameters.Add(jobParameter)  
    jobParameter.Value = "RunSSISPackage"  
  
    jobConnection.Open()  
    jobCommand.ExecuteNonQuery()  
    jobResult = DirectCast(jobCommand.Parameters("@RETURN_VALUE").Value, Integer)  
    jobConnection.Close()  
  
    Select Case jobResult  
      Case 0  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.")  
      Case Else  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.")  
    End Select  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace LaunchSSISPackageAgent_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      SqlConnection jobConnection;  
      SqlCommand jobCommand;  
      SqlParameter jobReturnValue;  
      SqlParameter jobParameter;  
      int jobResult;  
  
      jobConnection = new SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI");  
      jobCommand = new SqlCommand("sp_start_job", jobConnection);  
      jobCommand.CommandType = CommandType.StoredProcedure;  
  
      jobReturnValue = new SqlParameter("@RETURN_VALUE", SqlDbType.Int);  
      jobReturnValue.Direction = ParameterDirection.ReturnValue;  
      jobCommand.Parameters.Add(jobReturnValue);  
  
      jobParameter = new SqlParameter("@job_name", SqlDbType.VarChar);  
      jobParameter.Direction = ParameterDirection.Input;  
      jobCommand.Parameters.Add(jobParameter);  
      jobParameter.Value = "RunSSISPackage";  
  
      jobConnection.Open();  
      jobCommand.ExecuteNonQuery();  
      jobResult = (Int32)jobCommand.Parameters["@RETURN_VALUE"].Value;  
      jobConnection.Close();  
  
      switch (jobResult)  
      {  
        case 0:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.");  
          break;  
        default:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.");  
          break;  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
 
  
###  <a name="using-a-web-service-or-remote-component-to-run-a-remote-package-programmatically"></a><a name="service"></a> <span data-ttu-id="46dfb-127">웹 서비스 또는 원격 구성 요소를 사용하여 프로그래밍 방식으로 원격 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="46dfb-127">Using a Web Service or Remote Component to Run a Remote Package Programmatically</span></span>  
 <span data-ttu-id="46dfb-128">서버에서 프로그래밍 방식으로 패키지를 실행하기 위한 이전 솔루션의 경우 서버에서 사용자 지정 코드가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-128">The previous solution for running packages programmatically on the server does not require any custom code on the server.</span></span> <span data-ttu-id="46dfb-129">그러나 SQL Server 에이전트를 사용하지 않고 패키지를 실행할 수 있는 솔루션이 필요한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-129">However, you may prefer a solution that does not rely on SQL Server Agent to execute packages.</span></span> <span data-ttu-id="46dfb-130">다음 예에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 로컬로 시작하기 위해 서버에 만들 수 있는 웹 서비스와 클라이언트 컴퓨터에서 웹 서비스를 호출하는 데 사용할 수 있는 테스트 애플리케이션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-130">The following example demonstrates a Web service that can be created on the server to start [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages locally, and a test application that can be used to call the Web service from a client computer.</span></span> <span data-ttu-id="46dfb-131">웹 서비스 대신 원격 구성 요소를 만들려면 원격 구성 요소를 거의 변경하지 않는 동일한 코드 논리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-131">If you prefer to create a remote component instead of a Web service, you can use the same code logic with very few changes in a remote component.</span></span> <span data-ttu-id="46dfb-132">그러나 원격 구성 요소를 만들 경우에는 웹 서비스를 만들 때보다 더욱 광범위한 구성이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-132">However a remote component may require more extensive configuration than a Web service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="46dfb-133">인증 및 권한 부여에 기본 설정을 사용할 경우 웹 서비스에는 일반적으로 SQL Server 또는 파일 시스템에 액세스하여 패키지를 로드하고 실행할 수 있는 충분한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-133">With its default settings for authentication and authorization, a Web service generally does not have sufficient permissions to access SQL Server or the file system to load and execute packages.</span></span> <span data-ttu-id="46dfb-134">**web.config** 파일에서 인증 및 권한 부여 설정을 구성하고 데이터베이스 및 파일 시스템 권한을 적절하게 할당하여 웹 서비스에 적절한 권한을 할당해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-134">You may have to assign appropriate permissions to the Web service by configuring its authentication and authorization settings in the **web.config** file and assigning database and file system permissions as appropriate.</span></span> <span data-ttu-id="46dfb-135">웹, 데이터베이스 및 파일 시스템 사용 권한에 대한 자세한 설명은 이 항목에서 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-135">A complete discussion of Web, database, and file system permissions is beyond the scope of this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="46dfb-136">SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 ".", localhost 또는 로컬 서버의 서버 이름만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-136">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="46dfb-137">"(local)"은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-137">You cannot use "(local)".</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="46dfb-138">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="46dfb-138">Sample Code</span></span>  
 <span data-ttu-id="46dfb-139">다음 코드 예제에서는 웹 서비스를 만들고 테스트하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-139">The following code samples show how to create and test the Web service.</span></span>  
  
#### <a name="creating-the-web-service"></a><span data-ttu-id="46dfb-140">웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="46dfb-140">Creating the Web Service</span></span>  
 <span data-ttu-id="46dfb-141">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지는 파일 또는 SQL Server에서 직접 로드하거나 SQL Server와 특수한 파일 시스템 폴더 모두의 패키지 스토리지를 관리하는 SSIS 패키지 스토리지에서 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-141">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be loaded directly from a file, directly from SQL Server, or from the SSIS Package Store, which manages package storage in both SQL Server and special file system folders.</span></span> <span data-ttu-id="46dfb-142">이 예제에서는 `Select Case` 또는 `switch` 구문을 사용하여 패키지를 시작하기 위한 적절한 구문을 선택하고 입력 인수를 적절하게 연결함으로써 사용 가능한 모든 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-142">This sample supports all the available options by using a `Select Case` or `switch` construct to select the appropriate syntax for starting the package and to concatenate the input arguments appropriately.</span></span> <span data-ttu-id="46dfb-143">LaunchPackage 웹 서비스 메서드는 클라이언트 컴퓨터에서 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 어셈블리에 대한 참조가 필요하지 않도록 패키지 실행 결과를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 값 대신 정수로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-143">The LaunchPackage Web service method returns the result of package execution as an integer instead of a <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value so that client computers do not require a reference to any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] assemblies.</span></span>  
  
###### <a name="to-create-a-web-service-to-run-packages-on-the-server-programmatically"></a><span data-ttu-id="46dfb-144">웹 서비스를 만들어 서버에서 프로그래밍 방식으로 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="46dfb-144">To create a Web service to run packages on the server programmatically</span></span>  
  
1.  <span data-ttu-id="46dfb-145">Visual Studio를 열고 원하는 프로그래밍 언어로 웹 서비스 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-145">Open Visual Studio and create a Web service project in your preferred programming language.</span></span> <span data-ttu-id="46dfb-146">예제 코드에서는 프로젝트 이름으로 LaunchSSISPackageService를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-146">The sample code uses the name LaunchSSISPackageService for the project.</span></span>  
  
2.  <span data-ttu-id="46dfb-147">에 대 한 참조를 추가 하 `Microsoft.SqlServer.ManagedDTS` 고 `Imports` 또는 `using` 문을 코드 파일에 **Microsoft.SqlServer.Dts.Runtime** 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-147">Add a reference to `Microsoft.SqlServer.ManagedDTS` and add an `Imports` or `using` statement to the code file for the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
3.  <span data-ttu-id="46dfb-148">LaunchPackage 웹 서비스 메서드의 예제 코드를 클래스에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-148">Paste the sample code for the LaunchPackage Web service method into the class.</span></span> <span data-ttu-id="46dfb-149">이 예제에서는 코드 창의 전체 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-149">(The sample shows the whole contents of the code window.)</span></span>  
  
4.  <span data-ttu-id="46dfb-150">LaunchPackage 메서드의 입력 인수 중 기존 패키지를 가리키는 인수에 올바른 값을 지정하여 웹 서비스를 빌드하고 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-150">Build and test the Web service by providing a set of valid values for the input arguments of the LaunchPackage method that point to an existing package.</span></span> <span data-ttu-id="46dfb-151">예를 들어 package1.dtsx가 서버의 C:\My Packages에 저장되어 있는 경우 sourceType 값으로 "file"을 전달하고, sourceLocation 값으로 "C:\My Packages"를 전달하고, packageName 값으로 "package1"(확장명 없음)을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-151">For example, if package1.dtsx is stored on the server in C:\My Packages, pass "file" as the value of the sourceType, "C:\My Packages" as the value of sourceLocation, and "package1" (without the extension) as the value of packageName.</span></span>  
  
```vb  
Imports System.Web  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.IO  
  
<WebService(Namespace:="http://dtsue/")> _  
<WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
<Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
Public Class LaunchSSISPackageService  
  Inherits System.Web.Services.WebService  
  
  ' LaunchPackage Method Parameters:  
  ' 1. sourceType: file, sql, dts  
  ' 2. sourceLocation: file system folder, (none), logical folder  
  ' 3. packageName: for file system, ".dtsx" extension is appended  
  
  <WebMethod()> _  
  Public Function LaunchPackage( _  
    ByVal sourceType As String, _  
    ByVal sourceLocation As String, _  
    ByVal packageName As String) As Integer 'DTSExecResult  
  
    Dim packagePath As String  
    Dim myPackage As Package  
    Dim integrationServices As New Application  
  
    ' Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName)  
  
    Select Case sourceType  
      Case "file"  
        ' Package is stored as a file.  
        ' Add extension if not present.  
        If String.IsNullOrEmpty(Path.GetExtension(packagePath)) Then  
          packagePath = String.Concat(packagePath, ".dtsx")  
        End If  
        If File.Exists(packagePath) Then  
          myPackage = integrationServices.LoadPackage(packagePath, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid file location: " & packagePath)  
        End If  
      Case "sql"  
        ' Package is stored in MSDB.  
        ' Combine logical path and package name.  
        If integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty) Then  
          myPackage = integrationServices.LoadFromSqlServer( _  
            packageName, "(local)", String.Empty, String.Empty, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case "dts"  
        ' Package is managed by SSIS Package Store.  
        ' Default logical paths are File System and MSDB.  
        If integrationServices.ExistsOnDtsServer(packagePath, ".") Then  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case Else  
        Throw New ApplicationException( _  
          "Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.")  
    End Select  
  
    Return myPackage.Execute()  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.IO;  
  
[WebService(Namespace = "http://dtsue/")]  
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
public class LaunchSSISPackageServiceCS : System.Web.Services.WebService  
{  
  public LaunchSSISPackageServiceCS()  
  {  
    }  
  
  // LaunchPackage Method Parameters:  
  // 1. sourceType: file, sql, dts  
  // 2. sourceLocation: file system folder, (none), logical folder  
  // 3. packageName: for file system, ".dtsx" extension is appended  
  
  [WebMethod]  
  public int LaunchPackage(string sourceType, string sourceLocation, string packageName)  
  {   
  
    string packagePath;  
    Package myPackage;  
    Application integrationServices = new Application();  
  
    // Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName);  
  
    switch(sourceType)  
    {  
      case "file":  
        // Package is stored as a file.  
        // Add extension if not present.  
        if (String.IsNullOrEmpty(Path.GetExtension(packagePath)))  
        {  
          packagePath = String.Concat(packagePath, ".dtsx");  
        }  
        if (File.Exists(packagePath))  
        {  
          myPackage = integrationServices.LoadPackage(packagePath, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid file location: "+packagePath);  
        }  
        break;  
      case "sql":  
        // Package is stored in MSDB.  
        // Combine logical path and package name.  
        if (integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty))  
        {  
          myPackage = integrationServices.LoadFromSqlServer(packageName, "(local)", String.Empty, String.Empty, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      case "dts":  
        // Package is managed by SSIS Package Store.  
        // Default logical paths are File System and MSDB.  
        if (integrationServices.ExistsOnDtsServer(packagePath, "."))  
        {  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      default:  
        throw new ApplicationException("Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.");  
    }  
  
    return (Int32)myPackage.Execute();  
  
  }  
  
}  
```  
  
#### <a name="testing-the-web-service"></a><span data-ttu-id="46dfb-152">웹 서비스 테스트</span><span class="sxs-lookup"><span data-stu-id="46dfb-152">Testing the Web Service</span></span>  
 <span data-ttu-id="46dfb-153">다음 예제 콘솔 애플리케이션에서는 웹 서비스를 사용하여 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-153">The following sample console application uses the Web service to run a package.</span></span> <span data-ttu-id="46dfb-154">웹 서비스의 LaunchPackage 메서드는 클라이언트 컴퓨터에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 어셈블리에 대한 참조가 필요하지 않도록 패키지 실행 결과를 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 값 대신 정수로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-154">The LaunchPackage method of the Web service returns the result of package execution as an integer instead of a <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value so that client computers do not require a reference to any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] assemblies.</span></span> <span data-ttu-id="46dfb-155">이 예제에서는 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 값을 미러링하는 값을 포함하는 프라이빗 열거형을 만들어 실행 결과를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-155">The sample creates a private enumeration whose values mirror the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> values to report the results of execution.</span></span>  
  
###### <a name="to-create-a-console-application-to-test-the-web-service"></a><span data-ttu-id="46dfb-156">콘솔 애플리케이션을 만들어 웹 서비스를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="46dfb-156">To create a console application to test the Web service</span></span>  
  
1.  <span data-ttu-id="46dfb-157">Visual Studio에서 원하는 프로그래밍 언어를 사용하여 웹 서비스 프로젝트가 들어 있는 솔루션에 새 콘솔 애플리케이션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-157">In Visual Studio, add a new console application, using your preferred programming language, to the same solution that contains the Web service project.</span></span> <span data-ttu-id="46dfb-158">예제 코드에서는 프로젝트 이름으로 LaunchSSISPackageTest를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-158">The sample code uses the name LaunchSSISPackageTest for the project.</span></span>  
  
2.  <span data-ttu-id="46dfb-159">새 콘솔 애플리케이션을 솔루션의 시작 프로젝트로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-159">Set the new console application as the startup project in the solution.</span></span>  
  
3.  <span data-ttu-id="46dfb-160">웹 서비스 프로젝트에 대한 웹 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-160">Add a Web reference for the Web service project.</span></span> <span data-ttu-id="46dfb-161">필요할 경우 예제 코드에서 웹 서비스 프록시 개체에 지정한 이름에 대한 변수 선언을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-161">If necessary, adjust the variable declaration in the sample code for the name that you assign to the Web service proxy object.</span></span>  
  
4.  <span data-ttu-id="46dfb-162">기본 루틴 및 프라이빗 열거형에 대한 예제 코드를 코드에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-162">Paste the sample code for the Main routine and the private enumeration into the code.</span></span> <span data-ttu-id="46dfb-163">이 예제에서는 코드 창의 전체 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-163">(The sample shows the whole contents of the code window.)</span></span>  
  
5.  <span data-ttu-id="46dfb-164">LaunchPackage 메서드를 호출하는 코드 줄을 편집하여 기존 패키지를 가리키는 입력 인수에 올바른 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-164">Edit the line of code that calls the LaunchPackage method to provide a set of valid values for the input arguments that point to an existing package.</span></span> <span data-ttu-id="46dfb-165">예를 들어 package1.dtsx가 서버의 C:\My Packages에 저장되어 있는 경우 `sourceType` 값으로 "file"을 전달하고, `sourceLocation` 값으로 "C:\My Packages"를 전달하고, `packageName` 값으로 "package1"(확장명 없음)을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="46dfb-165">For example, if package1.dtsx is stored on the server in C:\My Packages, pass "file" as the value of `sourceType`, "C:\My Packages" as the value of `sourceLocation`, and "package1" (without the extension) as the value of `packageName`.</span></span>  
  
```vb  
Module LaunchSSISPackageTest  
  
  Sub Main()  
  
    Dim launchPackageService As New LaunchSSISPackageService.LaunchSSISPackageService  
    Dim packageResult As Integer  
  
    Try  
      packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage")  
    Catch ex As Exception  
      ' The type of exception returned by a Web service is:  
      '  System.Web.Services.Protocols.SoapException  
      Console.WriteLine("The following exception occurred: " & ex.Message)  
    End Try  
  
    Console.WriteLine(CType(packageResult, PackageExecutionResult).ToString)  
    Console.ReadKey()  
  
  End Sub  
  
  Private Enum PackageExecutionResult  
    PackageSucceeded  
    PackageFailed  
    PackageCompleted  
    PackageWasCancelled  
  End Enum  
  
End Module  
```  
  
```csharp  
using System;  
  
namespace LaunchSSISPackageSvcTestCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS launchPackageService = new LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS();  
      int packageResult = 0;  
  
      try  
      {  
        packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage");  
      }  
      catch (Exception ex)  
      {  
        // The type of exception returned by a Web service is:  
        //  System.Web.Services.Protocols.SoapException  
        Console.WriteLine("The following exception occurred: " + ex.Message);  
      }  
  
      Console.WriteLine(((PackageExecutionResult)packageResult).ToString());  
      Console.ReadKey();  
  
    }  
  
    private enum PackageExecutionResult  
    {  
      PackageSucceeded,  
      PackageFailed,  
      PackageCompleted,  
      PackageWasCancelled  
    };  
  
  }  
}  
```  
  

  
## <a name="external-resources"></a><span data-ttu-id="46dfb-166">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="46dfb-166">External Resources</span></span>  
  
-   <span data-ttu-id="46dfb-167">technet.microsoft.com의 비디오 - [방법: SQL Server 에이전트를 사용하여 SSIS 패키지 실행 자동화(SQL Server 비디오)](https://technet.microsoft.com/sqlserver/ff686764.aspx)</span><span class="sxs-lookup"><span data-stu-id="46dfb-167">Video, [How to: Automate SSIS Package Execution by Using the SQL Server Agent (SQL Server Video)](https://technet.microsoft.com/sqlserver/ff686764.aspx), on technet.microsoft.com</span></span>  
  
<span data-ttu-id="46dfb-168">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="46dfb-168">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="46dfb-169">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="46dfb-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="46dfb-170">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="46dfb-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="46dfb-171">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="46dfb-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46dfb-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46dfb-172">See Also</span></span>  
 <span data-ttu-id="46dfb-173">[로컬 실행과 원격 실행의 차이점 이해](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="46dfb-173">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="46dfb-174">[프로그래밍 방식으로 로컬 패키지 로드 및 실행](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="46dfb-174">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 [<span data-ttu-id="46dfb-175">로컬 패키지의 출력 로드</span><span class="sxs-lookup"><span data-stu-id="46dfb-175">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
