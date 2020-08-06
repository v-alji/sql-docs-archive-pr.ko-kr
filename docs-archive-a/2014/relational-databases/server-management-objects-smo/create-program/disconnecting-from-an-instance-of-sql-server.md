---
title: SQL Server의 인스턴스에서 연결을 끊는 중 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3514fce8fb8f1ccc8bd1b54acfa27825eaebbd34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660462"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a><span data-ttu-id="ad26d-102">SQL Server 인스턴스에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="ad26d-102">Disconnecting from an Instance of SQL Server</span></span>
  <span data-ttu-id="ad26d-103">수동으로 SMO( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects) 개체를 닫고 연결을 끊을 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-103">Manually closing and disconnecting [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects is not required.</span></span> <span data-ttu-id="ad26d-104">필요에 따라 연결이 열리고 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-104">Connections are opened and closed as required.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="ad26d-105">연결 풀링</span><span class="sxs-lookup"><span data-stu-id="ad26d-105">Connection Pooling</span></span>  
 <span data-ttu-id="ad26d-106"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 메서드를 호출하면 연결이 자동으로 해제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-106">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not automatically released.</span></span> <span data-ttu-id="ad26d-107"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 메서드를 명시적으로 호출하여 연결 풀에 대한 연결을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-107">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method must be called explicitly to release the connection to the connection pool.</span></span> <span data-ttu-id="ad26d-108">풀링되지 않은 연결을 요청할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-108">Also, you can request a non-pooled connection.</span></span> <span data-ttu-id="ad26d-109">이 작업은 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 개체를 참조하는 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 속성의 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 속성을 설정하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-109">You do this by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property that references the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="ad26d-110">RMO에 대해 SQL Server 인스턴스에서 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="ad26d-110">Disconnecting from an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="ad26d-111">RMO를 사용하여 프로그래밍할 때 서버 연결을 닫는 방법은 SMO와는 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-111">Closing server connections when you are programming with RMO works slightly different from SMO.</span></span>  
  
 <span data-ttu-id="ad26d-112">RMO 개체에 대 한 서버 연결이 개체에 의해 유지 관리 되기 때문에 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rmo를 사용 하 여 프로그래밍할 때 인스턴스에서 연결을 끊을 때도이 개체가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-112">Because the server connection for an RMO object is maintained by the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, this object is also used when disconnecting from an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when you program by using RMO.</span></span> <span data-ttu-id="ad26d-113"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용하여 연결을 닫으려면 RMO 개체의 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-113">To close a connection by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method of the RMO object.</span></span> <span data-ttu-id="ad26d-114">연결이 닫힌 후에는 RMO 개체를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-114">After the connection has been closed, RMO objects cannot be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad26d-115">예제</span><span class="sxs-lookup"><span data-stu-id="ad26d-115">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a><span data-ttu-id="ad26d-116">Visual Basic에서 SMO 개체 닫기 및 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="ad26d-116">Closing and Disconnecting an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="ad26d-117">다음 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 개체 속성의 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 속성을 설정하여 풀링되지 않은 연결을 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-117">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a><span data-ttu-id="ad26d-118">Visual C#에서 SMO 개체 닫기 및 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="ad26d-118">Closing and Disconnecting an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="ad26d-119">다음 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 개체 속성의 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 속성을 설정하여 풀링되지 않은 연결을 요청하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad26d-119">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad26d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad26d-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
