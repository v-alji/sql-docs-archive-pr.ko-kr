---
title: SMO에서 연결 된 서버 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 58804e2be1edfa685a57f56c173c77a50e0f9126
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646861"
---
# <a name="using-linked-servers-in-smo"></a><span data-ttu-id="e18f9-102">SMO에서 연결된 서버 사용</span><span class="sxs-lookup"><span data-stu-id="e18f9-102">Using Linked Servers in SMO</span></span>
  <span data-ttu-id="e18f9-103">연결된 서버는 원격 서버의 OLE DB 데이터 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-103">A linked server represents an OLE DB data source on a remote server.</span></span> <span data-ttu-id="e18f9-104">원격 OLE DB 데이터 원본은 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 개체를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-104">Remote OLE DB data sources are linked to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span>  
  
 <span data-ttu-id="e18f9-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB 공급자를 사용 하 여 현재 인스턴스에 원격 데이터베이스 서버를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-105">Remote database servers can be linked to the current instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using an OLE DB Provider.</span></span> <span data-ttu-id="e18f9-106">SMO에서 연결된 서버는 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-106">In SMO, linked servers are represented by the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="e18f9-107"><xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> 속성은 <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> 개체 모음을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-107">The <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> property references a collection of <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> objects.</span></span> <span data-ttu-id="e18f9-108">이들은 연결된 서버와 연결을 설정하는 데 필요한 로그온 자격 증명을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-108">These store the logon credentials that are required to establish a connection with the linked server.</span></span>  
  
## <a name="ole-db-providers"></a><span data-ttu-id="e18f9-109">OLE-DB 공급자</span><span class="sxs-lookup"><span data-stu-id="e18f9-109">OLE-DB Providers</span></span>  
 <span data-ttu-id="e18f9-110">SMO에서 설치된 OLE-DB 공급자는 <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> 개체 모음으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-110">In SMO, installed OLE-DB providers are represented by a collection of <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e18f9-111">예제</span><span class="sxs-lookup"><span data-stu-id="e18f9-111">Example</span></span>  
 <span data-ttu-id="e18f9-112">다음 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-112">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="e18f9-113">자세한 내용은 visual studio [.net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 visual [Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e18f9-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a><span data-ttu-id="e18f9-114">Visual Basic에서 OLE-DB 공급자 서버에 대한 링크 만들기</span><span class="sxs-lookup"><span data-stu-id="e18f9-114">Creating a link to an OLE-DB Provider Server in Visual Basic</span></span>  
 <span data-ttu-id="e18f9-115">코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 개체를 사용하여 다른 유형의 데이터 원본에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB에 대한 링크를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-115">The code example shows how to create a link to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogeneous data source by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="e18f9-116">를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 제품 이름으로 지정 하면 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 공식 OLE DB 공급자 인 클라이언트 OLE DB 공급자를 사용 하 여 연결 된 서버에서 데이터에 액세스할 수 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-116">By specifying [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the product name, data is accessed on the linked server by using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB Provider, which is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a><span data-ttu-id="e18f9-117">Visual C#에서 OLE-DB 공급자 서버에 대한 링크 만들기</span><span class="sxs-lookup"><span data-stu-id="e18f9-117">Creating a link to an OLE-DB Provider Server in Visual C#</span></span>  
 <span data-ttu-id="e18f9-118">코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 개체를 사용하여 다른 유형의 데이터 원본에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB에 대한 링크를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-118">The code example shows how to create a link to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogeneous data source by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="e18f9-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 제품 이름으로 지정하면 공식 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 용 OLE DB 공급자인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB 공급자를 사용하여 연결된 서버에서 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-119">By specifying [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the product name, data is accessed on the linked server by using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB Provider, which is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a><span data-ttu-id="e18f9-120">PowerShell에서 OLE-DB 공급자 서버에 대한 링크 만들기</span><span class="sxs-lookup"><span data-stu-id="e18f9-120">Creating a link to an OLE-DB Provider Server in PowerShell</span></span>  
 <span data-ttu-id="e18f9-121">코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> 개체를 사용하여 다른 유형의 데이터 원본에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB에 대한 링크를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-121">The code example shows how to create a link to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, heterogeneous data source by using the <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> object.</span></span> <span data-ttu-id="e18f9-122">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 제품 이름으로 지정하면 공식 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 용 OLE DB 공급자인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB 공급자를 사용하여 연결된 서버에서 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e18f9-122">By specifying [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the product name, data is accessed on the linked server by using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB Provider, which is the official OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -ArgumentList $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.
$lsvr.ProductName = "SQL Server"
  
#Create the Database Object  
$lsvr.Create()
```  
