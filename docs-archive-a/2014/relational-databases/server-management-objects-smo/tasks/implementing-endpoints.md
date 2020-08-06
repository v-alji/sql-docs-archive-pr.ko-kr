---
title: 끝점 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 293a661c6e1ad6f6139e30e0824e99686af98f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739621"
---
# <a name="implementing-endpoints"></a><span data-ttu-id="5de77-102">엔드포인트 구현</span><span class="sxs-lookup"><span data-stu-id="5de77-102">Implementing Endpoints</span></span>
  <span data-ttu-id="5de77-103">엔드포인트는 기본적으로 요청을 수신할 수 있는 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-103">An endpoint is a service that can listen natively for requests.</span></span> <span data-ttu-id="5de77-104">SMO는 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 개체를 사용하여 다양한 유형의 엔드포인트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-104">SMO supports various types of endpoints by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object.</span></span> <span data-ttu-id="5de77-105">ph x="1" /&gt; 개체 인스턴스를 만들고 해당 속성을 설정하여 특정 프로토콜을 사용하는 특정 유형의 페이로드를 처리하는 엔드포인트 서비스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-105">You can create an endpoint service that handles a specific type of payload, which uses a specific protocol, by creating an instance of an <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object and setting its properties.</span></span>  
  
 <span data-ttu-id="5de77-106"><xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 속성을 사용하여 다음 페이로드 유형 중 하나를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-106">The <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object can be used to specify on of the following payload types:</span></span>  
  
-   <span data-ttu-id="5de77-107">데이터베이스 미러링</span><span class="sxs-lookup"><span data-stu-id="5de77-107">Database mirroring</span></span>  
  
-   <span data-ttu-id="5de77-108">SOAP(SOAP 엔드포인트에 대한 지원은 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 및 이전 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 버전에 있음)</span><span class="sxs-lookup"><span data-stu-id="5de77-108">SOAP (support for SOAP endpoints is present in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] and earlier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions)</span></span>  
  
-   <span data-ttu-id="5de77-109">Service Broker</span><span class="sxs-lookup"><span data-stu-id="5de77-109">Service Broker</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 <span data-ttu-id="5de77-110">또한 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 속성을 사용하여 다음 두 가지 지원 프로토콜을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-110">Also, the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property can be used to specify the following two supported protocols:</span></span>  
  
-   <span data-ttu-id="5de77-111">HTTP 프로토콜</span><span class="sxs-lookup"><span data-stu-id="5de77-111">HTTP protocol</span></span>  
  
-   <span data-ttu-id="5de77-112">TCP 프로토콜</span><span class="sxs-lookup"><span data-stu-id="5de77-112">TCP protocol</span></span>  
  
 <span data-ttu-id="5de77-113">페이로드 유형을 지정한 경우 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> 개체 속성을 사용하여 실제 페이로드를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-113">Having specified the type of payload, the actual payload can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> object property.</span></span> <span data-ttu-id="5de77-114"><xref:Microsoft.SqlServer.Management.Smo.Payload> 개체 속성은 지정된 유형의 페이로드 개체에 대한 참조를 제공하며 이에 대한 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-114">The <xref:Microsoft.SqlServer.Management.Smo.Payload> object property provides a reference to a payload object of the specified type, for which the properties can be modified.</span></span>  
  
 <span data-ttu-id="5de77-115"><xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> 개체의 경우 미러링 역할과 암호화 설정 여부를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-115">For the <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> object, you must specify the mirroring role and whether encryption is enabled.</span></span> <span data-ttu-id="5de77-116"><xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> 개체에는 메시지 전달, 허용되는 최대 연결 수 및 인증 모드에 대한 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-116">The <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> object requires information about message forwarding, maximum number of connections allowed and the authentication mode.</span></span> <span data-ttu-id="5de77-117"><xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> 개체에서는 클라이언트(저장 프로시저 및 사용자 정의 함수)에 사용할 수 있는 SOAP 페이로드 메서드를 지정하는 <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> 개체 속성을 비롯하여 다양한 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-117">The <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> object requires various properties to be set including the <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> object property that specifies the SOAP payload methods available to clients (stored procedures and user-defined functions).</span></span>  
  
 <span data-ttu-id="5de77-118">마찬가지로 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> 속성으로 지정된 유형의 프로토콜 개체를 참조하는 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 개체 속성을 사용하여 실제 프로토콜을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-118">Similarly, the actual protocol can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> object property that references a protocol object of the type specified by <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property.</span></span> <span data-ttu-id="5de77-119"><xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> 개체에는 제한된 IP 주소 목록과 포트, 웹 사이트 및 인증 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-119">The <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> object requires a list of restricted IP addresses, and port, website, and authentication information.</span></span> <span data-ttu-id="5de77-120"><xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> 개체에도 제한된 IP 주소 목록과 포트 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-120">The <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> object also requires a list of restricted IP addresses and port information.</span></span>  
  
 <span data-ttu-id="5de77-121">엔드포인트가 만들어지고 완전히 정의되었으면 데이터베이스 사용자, 그룹, 역할 및 로그온에 대해 액세스를 부여, 취소 및 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-121">When the endpoint has been created and fully defined, access can be granted to, revoked from, and denied to database users, groups, roles, and logons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5de77-122">예제</span><span class="sxs-lookup"><span data-stu-id="5de77-122">Example</span></span>  
 <span data-ttu-id="5de77-123">다음 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-123">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="5de77-124">자세한 내용은 visual studio [.net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 visual [Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5de77-124">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a><span data-ttu-id="5de77-125">Visual Basic에서 데이터베이스 미러링 엔드포인트 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="5de77-125">Creating a Database Mirroring Endpoint Service in Visual Basic</span></span>  
 <span data-ttu-id="5de77-126">코드 예제는 SMO에서 데이터베이스 미러링 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-126">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="5de77-127">이 작업은 데이터베이스 미러를 만들기 전에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-127">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="5de77-128">데이터베이스 미러를 만들려면 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 및 기타 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 속성을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="5de77-128">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a><span data-ttu-id="5de77-129">Visual C#에서 데이터베이스 미러링 엔드포인트 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="5de77-129">Creating a Database Mirroring Endpoint Service in Visual C#</span></span>  
 <span data-ttu-id="5de77-130">코드 예제는 SMO에서 데이터베이스 미러링 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-130">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="5de77-131">이 작업은 데이터베이스 미러를 만들기 전에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-131">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="5de77-132">데이터베이스 미러를 만들려면 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 및 기타 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 속성을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="5de77-132">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```csharp
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a><span data-ttu-id="5de77-133">PowerShell에서 데이터베이스 미러링 엔드포인트 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="5de77-133">Creating a Database Mirroring Endpoint Service in PowerShell</span></span>  
 <span data-ttu-id="5de77-134">코드 예제는 SMO에서 데이터베이스 미러링 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-134">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="5de77-135">이 작업은 데이터베이스 미러를 만들기 전에 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5de77-135">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="5de77-136">데이터베이스 미러를 만들려면 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 및 기타 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체의 속성을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="5de77-136">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a><span data-ttu-id="5de77-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5de77-137">See Also</span></span>  
 [<span data-ttu-id="5de77-138">데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5de77-138">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
