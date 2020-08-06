---
title: SQL Server의 인스턴스에 연결 하는 중 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
author: stevestein
ms.author: sstein
ms.openlocfilehash: efc21451f4a876c6edfe4a2389ca937d11bc5c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660464"
---
# <a name="connecting-to-an-instance-of-sql-server"></a><span data-ttu-id="01e32-102">SQL Server 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-102">Connecting to an Instance of SQL Server</span></span>
  <span data-ttu-id="01e32-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]SMO (Management Objects) 응용 프로그램의 첫 번째 프로그래밍 단계는 개체의 인스턴스를 만들고 인스턴스에 대 한 연결을 설정 하는 것입니다 <xref:Microsoft.SqlServer.Management.Smo.Server> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="01e32-103">The first programming step in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) application is to create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and to establish its connection to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="01e32-104">다음과 같은 세 가지 방법으로 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체의 인스턴스를 만들고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-104">You can create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and establish a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in three ways.</span></span> <span data-ttu-id="01e32-105">첫 번째는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체 변수를 사용하여 연결 정보를 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-105">The first is using a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable to provide the connection information.</span></span> <span data-ttu-id="01e32-106">두 번째는 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체 속성을 명시적으로 설정하여 연결 정보를 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-106">The second is to provide the connection information by explicitly setting the <xref:Microsoft.SqlServer.Management.Smo.Server> object properties.</span></span> <span data-ttu-id="01e32-107">세 번째는 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체 생성자에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 전달하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-107">The third is to pass the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span>  
  
 <span data-ttu-id="01e32-108">**ServerConnection 개체 사용**</span><span class="sxs-lookup"><span data-stu-id="01e32-108">**Using a ServerConnection object**</span></span>  
  
 <span data-ttu-id="01e32-109"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체 변수를 사용할 경우 연결 정보를 다시 사용할 수 있다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-109">The advantage of using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable is that the connection information can be reused.</span></span> <span data-ttu-id="01e32-110"><xref:Microsoft.SqlServer.Management.Smo.Server> 개체 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-110">Declare a <xref:Microsoft.SqlServer.Management.Smo.Server> object variable.</span></span> <span data-ttu-id="01e32-111">그런 다음 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 선언하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 이름 및 인증 모드와 같은 연결 정보를 사용하여 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-111">Then, declare a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object and set properties with connection information such as the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the authentication mode.</span></span> <span data-ttu-id="01e32-112">그리고 나서 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체 변수를 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체 생성자에 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-112">Then, pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable as a parameter to the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span> <span data-ttu-id="01e32-113">다른 서버 개체 간에는 연결을 동시에 공유하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-113">It is not recommended to share connections between different server objects at the same time.</span></span> <span data-ttu-id="01e32-114"><xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 메서드를 사용하여 기존 연결 문자열의 복사본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-114">Use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to get a copy of the existing connection settings.</span></span>  
  
 <span data-ttu-id="01e32-115">**Server 개체 속성을 명시적으로 설정**</span><span class="sxs-lookup"><span data-stu-id="01e32-115">**Setting Server object properties explicitly**</span></span>  
  
 <span data-ttu-id="01e32-116">또는 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체 변수를 선언하고 기본 생성자를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-116">Alternatively, you can declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and call the default constructor.</span></span> <span data-ttu-id="01e32-117">이 경우 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체가 모든 기본 연결 설정을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 기본 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-117">As is, the <xref:Microsoft.SqlServer.Management.Smo.Server> object tries to connect to the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with all the default connection settings.</span></span>  
  
 <span data-ttu-id="01e32-118">**Server 개체 생성자에 SQL Server 인스턴스 이름 제공**</span><span class="sxs-lookup"><span data-stu-id="01e32-118">**Providing the SQL Server instance name in the Server object constructor**</span></span>  
  
 <span data-ttu-id="01e32-119"><xref:Microsoft.SqlServer.Management.Smo.Server> 개체 변수를 선언하고 생성자에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 이름을 문자열 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-119">Declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and pass the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance name as a string parameter in the constructor.</span></span> <span data-ttu-id="01e32-120"><xref:Microsoft.SqlServer.Management.Smo.Server> 개체가 기본 연결 설정을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스와의 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-120">The <xref:Microsoft.SqlServer.Management.Smo.Server> object establishes a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the default connection settings.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="01e32-121">연결 풀링</span><span class="sxs-lookup"><span data-stu-id="01e32-121">Connection Pooling</span></span>  
 <span data-ttu-id="01e32-122">일반적으로 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 개체의 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 메서드는 호출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-122">It is typically not required to call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span> <span data-ttu-id="01e32-123">SMO는 필요한 경우 자동으로 연결을 설정하고 작업을 완료한 후에는 연결을 연결 풀로 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-123">SMO will automatically establish a connection when required, and release the connection to the connection pool after it has finished performing operations.</span></span> <span data-ttu-id="01e32-124"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 메서드를 호출하면 연결이 풀로 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-124">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not released to the pool.</span></span> <span data-ttu-id="01e32-125">이 경우 연결을 풀로 해제하려면 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 메서드를 명시적으로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-125">An explicit call to the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method is required to release the connection to the pool.</span></span> <span data-ttu-id="01e32-126">또는 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 개체의 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 속성을 설정하여 풀링되지 않은 연결을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-126">Additionally, you can request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="multithreaded-applications"></a><span data-ttu-id="01e32-127">다중 스레드 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="01e32-127">Multithreaded Applications</span></span>  
 <span data-ttu-id="01e32-128">다중 스레드 애플리케이션의 경우 각 스레드에서 별도의 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-128">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="01e32-129">RMO의 SQL Server 인스턴스 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-129">Connecting to an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="01e32-130">RMO(복제 관리 개체)는 SMO와는 약간 다른 방법으로 복제 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-130">Replication Management Objects (RMO) uses a slightly different method from SMO to connect to a replication server.</span></span>  
  
 <span data-ttu-id="01e32-131">RMO 프로그래밍 개체의 경우 `Microsoft.SqlServer.Management.Common` 네임스페이스에서 구현한 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-131">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object implemented by the `Microsoft.SqlServer.Management.Common` namespace.</span></span> <span data-ttu-id="01e32-132">이 서버 연결은 RMO 프로그래밍 개체와는 독립적으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-132">This connection to the server is made independently of an RMO programming object.</span></span> <span data-ttu-id="01e32-133">그런 다음에는 인스턴스 생성 중에 또는 개체의 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 할당하여 연결이 RMO 개체로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-133">It is then it is passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="01e32-134">이런 식으로 RMO 프로그래밍 개체와 연결 개체 인스턴스를 별도로 만들고 관리할 수 있으며 여러 RMO 프로그래밍 개체에서 단일 연결 개체를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-134">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="01e32-135">복제 서버에 대한 연결에는 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-135">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="01e32-136">지정된 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체에 대해 모든 연결 속성이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-136">All properties for the connection are defined for a specified <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="01e32-137">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 각 연결에 고유의 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-137">Each connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="01e32-138">서버에 연결하고 성공적으로 로그인하기 위해 모든 인증 정보를 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-138">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="01e32-139">연결 설정 시 기본적으로 Microsoft Windows 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-139">By default, connections are made by using Microsoft Windows Authentication.</span></span> <span data-ttu-id="01e32-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하려면 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A>를 False로 설정하고 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> 및 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A>를 올바른 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그온 및 암호로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-140">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to False and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="01e32-141">보안 자격 증명은 항상 안전하게 저장 및 처리되어야 하고 가능하면 런타임에 제공되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-141">Security credentials must always be stored and handled securely, and supplied at run time whenever possible.</span></span>  
  
-   <span data-ttu-id="01e32-142">연결을 RMO 프로그래밍 개체에 전달하기 전에 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-142">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method must be called before passing the connection to any RMO programming object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="01e32-143">예</span><span class="sxs-lookup"><span data-stu-id="01e32-143">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="01e32-144">Visual Basic에서 Windows 인증을 사용하여 SQL Server 로컬 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-144">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="01e32-145">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로컬 인스턴스에 연결하는 데는 많은 코드가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-145">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="01e32-146">대신 인증 방법 및 서버에 대한 기본 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-146">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="01e32-147">데이터 검색이 필요한 첫 번째 작업에서 연결이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-147">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="01e32-148">이 예제는 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 인증을 사용 하 여의 로컬 인스턴스에 연결 하는 .net 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-148">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB1](SMO How to#SMO_VB1)]  -->  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="01e32-149">Visual C#에서 Windows 인증을 사용하여 SQL Server 로컬 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-149">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="01e32-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로컬 인스턴스에 연결하는 데는 많은 코드가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-150">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="01e32-151">대신 인증 방법 및 서버에 대한 기본 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-151">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="01e32-152">데이터 검색이 필요한 첫 번째 작업에서 연결이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-152">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="01e32-153">다음 예는 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로컬 인스턴스에 연결하는 Visual C# .NET 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-153">This example is Visual C# .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="01e32-154">Visual Basic .NET에서 Windows 인증을 사용하여 SQL Server 원격 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-154">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="01e32-155">Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결할 경우에는 인증 유형을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-155">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="01e32-156">Windows 인증이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-156">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="01e32-157">이 예제는 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows 인증을 사용 하 여 원격 인스턴스에 연결 하는 .net 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-157">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="01e32-158">*Strserver* 문자열 변수에는 원격 인스턴스의 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-158">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB2](SMO How to#SMO_VB2)]  -->  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="01e32-159">Visual C#에서 Windows 인증을 사용하여 SQL Server 원격 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-159">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="01e32-160">Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결할 경우에는 인증 유형을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-160">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="01e32-161">Windows 인증이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-161">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="01e32-162">다음 예는 Windows 인증을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 원격 인스턴스에 연결하는 Visual C# .NET 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-162">This example is Visual C# .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="01e32-163">*Strserver* 문자열 변수에는 원격 인스턴스의 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-163">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
```  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a><span data-ttu-id="01e32-164">Visual Basic에서 SQL Server 인증을 사용하여 SQL Server 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-164">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual Basic</span></span>  
 <span data-ttu-id="01e32-165">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결할 경우에는 인증 유형을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-165">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="01e32-166">다음 예에서는 연결 정보를 다시 사용할 수 있도록 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체 변수를 선언하는 다른 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-166">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="01e32-167">예는 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 원격 및 *vpassword* 에 연결 하는 방법을 보여 주는 .net 코드는 로그온 및 암호를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-167">The example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a><span data-ttu-id="01e32-168">Visual C#에서 SQL Server 인증을 사용하여 SQL Server 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="01e32-168">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual C#</span></span>  
 <span data-ttu-id="01e32-169">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결할 경우에는 인증 유형을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-169">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="01e32-170">다음 예에서는 연결 정보를 다시 사용할 수 있도록 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체 변수를 선언하는 다른 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-170">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="01e32-171">예제는 원격 및 *Vpassword* 에 연결 하는 방법을 보여 주는 Visual c # .net 코드는 로그온 및 암호를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="01e32-171">The example is Visual C# .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="01e32-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01e32-172">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
