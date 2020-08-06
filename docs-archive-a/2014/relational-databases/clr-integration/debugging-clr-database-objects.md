---
title: CLR 데이터베이스 개체 디버깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 084b2494ec55b502f71154ca1f174a6de6d2ab70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638837"
---
# <a name="debugging-clr-database-objects"></a><span data-ttu-id="d3123-102">CLR 데이터베이스 개체 디버깅</span><span class="sxs-lookup"><span data-stu-id="d3123-102">Debugging CLR Database Objects</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d3123-103">는 데이터베이스의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 및 CLR(공용 언어 런타임) 개체 디버깅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-103">provides support for debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="d3123-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 디버깅에서 중요한 점은, 설치 및 사용이 쉽고 SQL Server 디버거를 Microsoft Visual Studio 디버거와 통합할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-104">The key aspects of debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are the ease of setup and use, and the integration of the SQL Server debugger with the Microsoft Visual Studio debugger.</span></span> <span data-ttu-id="d3123-105">또한 디버깅이 여러 언어에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-105">Furthermore, debugging works across languages.</span></span> <span data-ttu-id="d3123-106">사용자는 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 CLR 개체로 매끄럽게 한 단계씩 코드를 실행할 수 있으며 그 반대의 경우도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-106">Users can step seamlessly into CLR objects from [!INCLUDE[tsql](../../../includes/tsql-md.md)], and vice versa.</span></span> <span data-ttu-id="d3123-107">관리되는 데이터베이스 개체를 디버깅할 때는 SQL Server Management Studio의 Transact-SQL 디버거를 사용할 수 없지만 Visual Studio의 디버거를 사용하여 개체를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-107">The Transact-SQL debugger in SQL Server Management Studio cannot be used to debug managed database objects, but you can debug the objects by using the debuggers in Visual Studio.</span></span> <span data-ttu-id="d3123-108">Visual Studio의 관리되는 데이터베이스 개체 디버깅은 서버에서 실행 중인 루틴에서 "step into" 및 "step over" 문과 같은 대부분의 일반적인 디버깅 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-108">Managed database object debugging in Visual Studio supports all common debugging features, such as "step into" and "step over" statements within routines executing on the server.</span></span> <span data-ttu-id="d3123-109">디버거는 디버깅하는 동안 중단점을 설정하고, 호출 스택을 검사하고, 변수를 검사하고, 변수 값을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-109">Debuggers can set breakpoints, inspect the call stack, inspect variables, and modify variable values while debugging.</span></span> <span data-ttu-id="d3123-110">Visual Studio .NET 2003은 CLR 통합 프로그래밍 또는 디버깅에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-110">Note that Visual Studio .NET 2003 cannot be used for CLR integration programming or debugging.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d3123-111">에는 .NET Framework가 미리 설치되어 있으며 Visual Studio .NET 2003에서는 .NET Framework 2.0 어셈블리를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-111">includes the .NET Framework pre-installed, and Visual Studio .NET 2003 cannot use the .NET Framework 2.0 assemblies.</span></span>  
  
 <span data-ttu-id="d3123-112">Visual Studio를 사용 하 여 관리 코드를 디버깅 하는 방법에 대 한 자세한 내용은 Visual Studio 설명서의 "[관리 코드 디버깅](https://go.microsoft.com/fwlink/?LinkId=120377)" 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3123-112">For more information about debugging managed code using Visual Studio, see the "[Debugging Managed Code](https://go.microsoft.com/fwlink/?LinkId=120377)" topic in the Visual Studio documentation.</span></span>  
  
## <a name="debugging-permissions-and-restrictions"></a><span data-ttu-id="d3123-113">디버깅 권한 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="d3123-113">Debugging Permissions and Restrictions</span></span>  
 <span data-ttu-id="d3123-114">디버깅은 높은 권한의 작업 이므로 **sysadmin** 고정 서버 역할의 멤버만에서이 작업을 수행할 수 있습니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d3123-114">Debugging is a highly privileged operation, and therefore only members of the **sysadmin** fixed server role are allowed to do so in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d3123-115">디버깅하는 동안에는 다음 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-115">The following restrictions apply while debugging:</span></span>  
  
-   <span data-ttu-id="d3123-116">CLR 루틴 디버깅은 한 번에 하나의 디버거 인스턴스로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-116">Debugging CLR routines is restricted to one debugger instance at a time.</span></span> <span data-ttu-id="d3123-117">이 제한이 적용되는 이유는, 중단점에 도달하면 모든 CLR 코드 실행이 중지되고 이 중단점에서 디버거가 전진할 때까지 실행이 멈추기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-117">This limitation applies because all CLR code execution freezes when a break point is hit and execution does not continue until the debugger advances from the break point.</span></span> <span data-ttu-id="d3123-118">하지만 다른 연결에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 디버깅을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-118">However, you can continue debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] in other connections.</span></span> <span data-ttu-id="d3123-119">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 디버깅은 서버의 다른 실행을 중지하지는 않지만 잠금을 보유함으로써 다른 연결들을 기다리게 만드는 원인이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-119">Although [!INCLUDE[tsql](../../../includes/tsql-md.md)] debugging does not freeze other executions on the server, it could cause other connections to wait by holding a lock.</span></span>  
  
-   <span data-ttu-id="d3123-120">기존 연결은 디버깅할 수 없습니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 연결을 만들려면 클라이언트 및 디버거 환경에 대한 정보가 필요하므로 새 연결만 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-120">Existing connections cannot be debugged, only new connections, as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requires information about the client and debugger environment before the connection can be made.</span></span>  
  
 <span data-ttu-id="d3123-121">위의 제한 사항으로 인해 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 및 CLR 코드를 테스트 서버에서 디버깅하는 것이 좋습니다. 프로덕션 서버는 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d3123-121">Due to the above restrictions, we recommend that [!INCLUDE[tsql](../../../includes/tsql-md.md)] and CLR code be debugged on a test server, and not on a production server.</span></span>  
  
## <a name="overview-of-debugging-managed-database-objects"></a><span data-ttu-id="d3123-122">관리되는 데이터베이스 개체 디버깅 개요</span><span class="sxs-lookup"><span data-stu-id="d3123-122">Overview of Debugging Managed Database Objects</span></span>  
 <span data-ttu-id="d3123-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 디버깅은 각 연결 모델을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-123">Debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follows a per-connection model.</span></span> <span data-ttu-id="d3123-124">디버거는 자신이 연결된 클라이언트 연결에 대해서만 작업을 감지하고 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-124">A debugger can detect and debug activities only to the client connection to which it is attached.</span></span> <span data-ttu-id="d3123-125">디버거 기능은 연결 유형의 제한을 받지 않으므로 TDS(Tabular Data Stream) 및 HTTP 연결을 모두 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-125">Because the functionality of the debugger is not limited by the type of connection, both tabular data stream (TDS) and HTTP connections can be debugged.</span></span> <span data-ttu-id="d3123-126">하지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 기존 연결 디버깅은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not allow debugging existing connections.</span></span> <span data-ttu-id="d3123-127">디버깅은 서버에서 실행 중인 루틴에서 대부분의 일반적인 디버깅 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-127">Debugging supports all common debugging features within routines executing on the server.</span></span> <span data-ttu-id="d3123-128">디버거와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 간의 상호 작용은 분산 COM(구성 요소 개체 모델)을 통해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-128">The interaction between a debugger and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] happens through distributed Component Object Model (COM).</span></span>  
  
 <span data-ttu-id="d3123-129">관리 되는 저장 프로시저, 함수, 트리거, 사용자 정의 형식 및 집계를 디버깅 하는 방법에 대 한 자세한 내용 및 시나리오는 Visual Studio 설명서의 "[SQL SERVER CLR 통합 데이터베이스 디버깅](https://go.microsoft.com/fwlink/?LinkId=120378)" 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3123-129">For more information and scenarios about debugging managed stored procedures, functions, triggers, user-defined types, and aggregates, see the "[SQL Server CLR Integration Database Debugging](https://go.microsoft.com/fwlink/?LinkId=120378)" topic in the Visual Studio documentation.</span></span>  
  
 <span data-ttu-id="d3123-130">Visual Studio를 원격 개발, 디버깅 및 개발에 사용하려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 TCP/IP 네트워크 프로토콜을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-130">The TCP/IP network protocol must be enabled on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in order to use Visual Studio for remote development, debugging, and development.</span></span> <span data-ttu-id="d3123-131">서버에서 TCP/IP 프로토콜을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d3123-131">For more information about enabling TCP/IP protocol on the server, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
  
#### <a name="to-debug-a-managed-database-object"></a><span data-ttu-id="d3123-132">관리되는 데이터베이스 개체를 디버깅하려면</span><span class="sxs-lookup"><span data-stu-id="d3123-132">To debug a managed database object</span></span>  
  
1.  <span data-ttu-id="d3123-133">Microsoft Visual Studio를 열고 새 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 프로젝트를 만든 다음 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 데이터베이스에 대한 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-133">Open Microsoft Visual Studio, create a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] project, and establish a connection to a database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="d3123-134">새 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-134">Create a new type.</span></span> <span data-ttu-id="d3123-135">**솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가** 및 **새 항목** ...을 선택 합니다. **새 항목 추가** 창에서 **저장 프로시저**, **사용자 정의 함수**, **사용자 정의 형식**, **트리거**, **집계**또는 **클래스**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-135">In **Solution Explorer**, right-click the project, select **Add** and **New Item...** From the **Add New Item** window, select **Stored Procedure**, **User-Defined Function**, **User-Defined Type**, **Trigger**, **Aggregate**, or **Class**.</span></span> <span data-ttu-id="d3123-136">새 형식의 원본 파일 이름을 지정 하 고 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-136">Specify a name for the source file of the new type and click **Add**.</span></span>  
  
3.  <span data-ttu-id="d3123-137">새 형식의 코드를 텍스트 편집기에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-137">Add code for the new type to the text editor.</span></span> <span data-ttu-id="d3123-138">저장 프로시저의 예제 코드는 이 항목의 뒷부분에 나오는 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3123-138">For sample code for an example stored procedure, see the section later in this topic.</span></span>  
  
4.  <span data-ttu-id="d3123-139">형식을 테스트하는 스크립트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-139">Add a script that tests the type.</span></span> <span data-ttu-id="d3123-140">**솔루션 탐색기**에서 **테스트** 스크립트 디렉터리를 확장 하 **고 test.sql를** 두 번 클릭 하 여 기본 테스트 스크립트 원본 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-140">In **Solution Explorer**, expand the **TestScripts** directory double-click **Test.sql** to open the default test script source file.</span></span> <span data-ttu-id="d3123-141">디버깅할 코드를 호출하는 테스트 스크립트 하나를 텍스트 편집기에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-141">Add the test script, one that invokes the code to be debugged, to the text editor.</span></span> <span data-ttu-id="d3123-142">예제 스크립트는 아래를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3123-142">See below for a sample script.</span></span>  
  
5.  <span data-ttu-id="d3123-143">원본 코드에 중단점을 하나 이상 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-143">Place one or more breakpoints in the source code.</span></span> <span data-ttu-id="d3123-144">디버그 하려는 함수 또는 루틴 내에서 텍스트 편집기의 코드 줄을 마우스 오른쪽 단추로 클릭 하 고 **중단점** 및 **중단점 삽입**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-144">Right-click on a line of code in the text editor, within the function or routine you want to debug, and select **Breakpoint** and **Insert Breakpoint**.</span></span> <span data-ttu-id="d3123-145">중단점이 추가되어 코드 줄이 빨간색으로 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-145">The breakpoint is added, highlighting the line of code in red.</span></span>  
  
6.  <span data-ttu-id="d3123-146">**디버그** 메뉴에서 **디버깅 시작** 을 선택 하 여 프로젝트를 컴파일, 배포 및 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-146">In the **Debug** menu, select **Start Debugging** to compile, deploy, and test the project.</span></span> <span data-ttu-id="d3123-147">Test.sql의 테스트 스크립트가 실행되고 관리되는 데이터베이스 개체가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-147">The test script in Test.sql will be run and the managed database object will be invoked.</span></span>  
  
7.  <span data-ttu-id="d3123-148">명령 포인터를 가리키는 노란색 화살표가 중단점에 나타나면 코드 실행이 중지되고 관리되는 데이터베이스 개체의 디버깅을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-148">When the yellow arrow designating the instruction pointer appears at the breakpoint code execution pauses and you can begin debugging your managed database object.</span></span> <span data-ttu-id="d3123-149">**디버그** 메뉴에서 한 **단계씩 코드 실행** 하 여 명령 포인터를 다음 코드 줄로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-149">You can **Step Over** from the **Debug** menu to advance the instruction pointer to the next line of code.</span></span> <span data-ttu-id="d3123-150">**지역** 창은 현재 명령 포인터로 강조 표시 된 개체의 상태를 관찰 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-150">The **Locals** window is used to observe the state of the objects currently highlighted by the instruction pointer.</span></span> <span data-ttu-id="d3123-151">**조사식** 창에 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-151">Variables can be added to the **Watch** window.</span></span> <span data-ttu-id="d3123-152">그러면 변수가 현재 명령 포인터로 강조 표시된 코드 줄에 있을 때뿐만 아니라 전체 디버깅 세션에 걸쳐 조사 변수의 상태를 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-152">The state of watched variables can be observed throughout the entire debugging session, not only when the variable is in the line of code currently highlighted by instruction pointer.</span></span> <span data-ttu-id="d3123-153">명령 포인터를 다음 중단점으로 전진하려면 디버그 메뉴에서 계속을 선택하고, 또는 더 이상 중단점이 없으면 루틴 실행을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-153">Select Continue from the Debug menu to advance the instruction pointer to the next breakpoint or to complete execution of the routine if there are no more breakpoints.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3123-154">예제</span><span class="sxs-lookup"><span data-stu-id="d3123-154">Example</span></span>  
 <span data-ttu-id="d3123-155">다음 예에서는 호출자에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-155">The following example returns the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version to the caller.</span></span>  
  
 <span data-ttu-id="d3123-156">C#</span><span class="sxs-lookup"><span data-stu-id="d3123-156">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="d3123-157">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3123-157">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="d3123-158">다음은 위에 정의된 GetVersion 저장 프로시저를 호출하는 테스트 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d3123-158">The following is a test script that invokes the GetVersion stored procedure defined above.</span></span>  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3123-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3123-159">See Also</span></span>  
 [<span data-ttu-id="d3123-160">CLR&#40;공용 언어 런타임&#41; 통합 프로그래밍 개요</span><span class="sxs-lookup"><span data-stu-id="d3123-160">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
