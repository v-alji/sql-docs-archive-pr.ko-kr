---
title: 프로그래밍 방식으로 연결 추가 | Microsoft Docs
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
- connection managers [Integration Services], packages
- Integration Services packages, connections
- connections [Integration Services], packages
- SSIS packages, connections
- packages [Integration Services], connections
- intrinsic properties [Integration Services]
- SQL Server Integration Services packages, connections
- ConnectionManager class
- SSIS connection managers
- adding package connections
ms.assetid: d90716d1-4c65-466c-b82c-4aabbee1e3e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5952221dbf2689d2328695baf965ce884dc07fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649649"
---
# <a name="adding-connections-programmatically"></a><span data-ttu-id="e202c-102">프로그래밍 방식으로 연결 추가</span><span class="sxs-lookup"><span data-stu-id="e202c-102">Adding Connections Programmatically</span></span>
  <span data-ttu-id="e202c-103"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 클래스는 외부 데이터 원본에 대한 실제 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-103">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class represents physical connections to external data sources.</span></span> <span data-ttu-id="e202c-104"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 클래스는 연결의 구현 세부 사항을 런타임에서 격리합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-104">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class isolates the implementation details of the connection from the runtime.</span></span> <span data-ttu-id="e202c-105">이 클래스를 사용하면 런타임에서는 일관되고 예측 가능한 방식으로 각 연결 관리자와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-105">This enables the runtime to interact with each connection manager in a consistent and predictable manner.</span></span> <span data-ttu-id="e202c-106">연결 관리자에는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>과 같이 모든 연결에 공통된 스톡 속성 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-106">Connection managers contain a set of stock properties that all connections have in common, such as the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>.</span></span> <span data-ttu-id="e202c-107">그러나 연결 관리자를 구성하는 데는 일반적으로 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> 속성만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-107">However, the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> properties are ordinarily the only properties required to configure a connection manager.</span></span> <span data-ttu-id="e202c-108">연결 클래스에서 `Open` 또는 `Connect`와 같은 메서드를 제공하여 데이터 원본에 대한 실제 연결을 설정하는 다른 프로그래밍 패러다임과 달리 런타임 엔진에서는 패키지 실행 중 패키지의 모든 연결을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-108">Unlike other programming paradigms, where connection classes expose methods such as `Open` or `Connect` to physically establish a connection to the data source, the run-time engine manages all the connections for the package while it runs.</span></span>  
  
 <span data-ttu-id="e202c-109"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> 클래스는 해당 패키지에 추가되었으며 런타임에 사용할 수 있는 연결 관리자의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-109">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> class is a collection of the connection managers that have been added to that package and are available for use at run time.</span></span> <span data-ttu-id="e202c-110">컬렉션의 <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> 메서드를 사용하고 연결 관리자 유형을 나타내는 문자열을 지정하여 컬렉션에 연결 관리자를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-110">You can add more connection managers to the collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method of the collection, and supplying a string that indicates the connection manager type.</span></span> <span data-ttu-id="e202c-111"><xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> 메서드는 패키지에 추가된 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-111">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method returns the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> instance that was added to the package.</span></span>  
  
## <a name="intrinsic-properties"></a><span data-ttu-id="e202c-112">기본 속성</span><span class="sxs-lookup"><span data-stu-id="e202c-112">Intrinsic Properties</span></span>  
 <span data-ttu-id="e202c-113"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 클래스는 모든 연결에 공통된 속성 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-113">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class exposes a set of properties that are common to all connections.</span></span> <span data-ttu-id="e202c-114">그러나 특정 연결 유형에 고유한 속성에 액세스해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-114">However, sometimes you need access to properties that are unique to the specific connection type.</span></span> <span data-ttu-id="e202c-115"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 컬렉션을 사용하면 이러한 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class provides access to these properties.</span></span> <span data-ttu-id="e202c-116">이러한 속성을 검색하는 데는 인덱서나 속성 이름 및 **GetValue** 메서드를 사용할 수 있으며, 해당 값을 설정하는 데는 **SetValue** 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-116">The properties can be retrieved from the collection using the indexer or the property name and the **GetValue** method, and the values are set using the **SetValue** method.</span></span> <span data-ttu-id="e202c-117">기본 연결 개체의 속성은 개체의 실제 인스턴스를 가져오고 해당 속성을 직접 설정하는 방법으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-117">The properties of the underlying connection object properties can also be set by acquiring an actual instance of the object and setting its properties directly.</span></span> <span data-ttu-id="e202c-118">기본 연결을 가져오려면 연결 관리자의 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-118">To get the underlying connection, use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> property of the connection manager.</span></span> <span data-ttu-id="e202c-119">다음 코드 줄에서는 기본 클래스 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>가 있는 ADO.NET 연결 관리자를 만드는 C# 줄을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-119">The following line of code shows a C# line that creates an ADO.NET connection manager that has the underlying class, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>.</span></span>  
  
 `ConnectionManagerAdoNetClass cmado = cm.InnerObject as ConnectionManagerAdoNet;`  
  
 <span data-ttu-id="e202c-120">이 코드 줄은 관리되는 연결 관리자 개체를 기본 연결 개체로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-120">This casts the managed connection manager object to its underlying connection object.</span></span> <span data-ttu-id="e202c-121">C++를 사용하는 경우에는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 개체의 `QueryInterface` 메서드를 호출하며 기본 연결 개체의 인터페이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-121">If you are using C++, the `QueryInterface` method of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object is called and the interface of the underlying connection object is requested.</span></span>  
  
 <span data-ttu-id="e202c-122">다음 표에서는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 연결 관리자와</span><span class="sxs-lookup"><span data-stu-id="e202c-122">The following table lists the connection managers included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="e202c-123">`package.Connections.Add("xxx")` 문에 사용되는 문자열을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-123">and the string that is used in the `package.Connections.Add("xxx")` statement.</span></span> <span data-ttu-id="e202c-124">모든 연결 관리자의 목록은 [Integration Services&#40;SSIS&#41; 연결](../connection-manager/integration-services-ssis-connections.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e202c-124">For a list of all connection managers, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
|<span data-ttu-id="e202c-125">String</span><span class="sxs-lookup"><span data-stu-id="e202c-125">String</span></span>|<span data-ttu-id="e202c-126">ODBC 대상 편집기</span><span class="sxs-lookup"><span data-stu-id="e202c-126">Connection manager</span></span>|  
|------------|------------------------|  
|<span data-ttu-id="e202c-127">"OLEDB"</span><span class="sxs-lookup"><span data-stu-id="e202c-127">"OLEDB"</span></span>|<span data-ttu-id="e202c-128">OLE DB 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-128">Connection manager for OLE DB connections.</span></span>|  
|<span data-ttu-id="e202c-129">"ODBC"</span><span class="sxs-lookup"><span data-stu-id="e202c-129">"ODBC"</span></span>|<span data-ttu-id="e202c-130">ODBC 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-130">Connection manager for ODBC connections.</span></span>|  
|<span data-ttu-id="e202c-131">"ADO"</span><span class="sxs-lookup"><span data-stu-id="e202c-131">"ADO"</span></span>|<span data-ttu-id="e202c-132">ADO 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-132">Connection manager for ADO connections.</span></span>|  
|<span data-ttu-id="e202c-133">"ADO.NET:SQL"</span><span class="sxs-lookup"><span data-stu-id="e202c-133">"ADO.NET:SQL"</span></span>|<span data-ttu-id="e202c-134">ADO.NET(SQL 데이터 공급자) 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-134">Connection manager for ADO.NET (SQL data provider) connections.</span></span>|  
|<span data-ttu-id="e202c-135">"ADO.NET:OLEDB"</span><span class="sxs-lookup"><span data-stu-id="e202c-135">"ADO.NET:OLEDB"</span></span>|<span data-ttu-id="e202c-136">ADO.NET(OLE DB 데이터 공급자) 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-136">Connection manager for ADO.NET (OLE DB data provider) connections.</span></span>|  
|<span data-ttu-id="e202c-137">"FLATFILE"</span><span class="sxs-lookup"><span data-stu-id="e202c-137">"FLATFILE"</span></span>|<span data-ttu-id="e202c-138">플랫 파일 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-138">Connection manager for flat file connections.</span></span>|  
|<span data-ttu-id="e202c-139">"FILE"</span><span class="sxs-lookup"><span data-stu-id="e202c-139">"FILE"</span></span>|<span data-ttu-id="e202c-140">파일 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-140">Connection manager for file connections.</span></span>|  
|<span data-ttu-id="e202c-141">"MULTIFLATFILE"</span><span class="sxs-lookup"><span data-stu-id="e202c-141">"MULTIFLATFILE"</span></span>|<span data-ttu-id="e202c-142">다중 플랫 파일 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-142">Connection manager for multiple flat file connections.</span></span>|  
|<span data-ttu-id="e202c-143">"MULTIFILE"</span><span class="sxs-lookup"><span data-stu-id="e202c-143">"MULTIFILE"</span></span>|<span data-ttu-id="e202c-144">다중 파일 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-144">Connection manager for multiple file connections.</span></span>|  
|<span data-ttu-id="e202c-145">"SQLMOBILE"</span><span class="sxs-lookup"><span data-stu-id="e202c-145">"SQLMOBILE"</span></span>|<span data-ttu-id="e202c-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-146">Connection manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connections.</span></span>|  
|<span data-ttu-id="e202c-147">"MSOLAP100"</span><span class="sxs-lookup"><span data-stu-id="e202c-147">"MSOLAP100"</span></span>|<span data-ttu-id="e202c-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-148">Connection manager for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connections.</span></span>|  
|<span data-ttu-id="e202c-149">"FTP"</span><span class="sxs-lookup"><span data-stu-id="e202c-149">"FTP"</span></span>|<span data-ttu-id="e202c-150">FTP 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-150">Connection manager for FTP connections.</span></span>|  
|<span data-ttu-id="e202c-151">"HTTP"</span><span class="sxs-lookup"><span data-stu-id="e202c-151">"HTTP"</span></span>|<span data-ttu-id="e202c-152">HTTP 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-152">Connection manager for HTTP connections.</span></span>|  
|<span data-ttu-id="e202c-153">"MSMQ"</span><span class="sxs-lookup"><span data-stu-id="e202c-153">"MSMQ"</span></span>|<span data-ttu-id="e202c-154">메시지 큐(MSMQ) 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-154">Connection manager for Message Queuing (also known as MSMQ) connections.</span></span>|  
|<span data-ttu-id="e202c-155">"SMTP"</span><span class="sxs-lookup"><span data-stu-id="e202c-155">"SMTP"</span></span>|<span data-ttu-id="e202c-156">SMTP 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-156">Connection manager for SMTP connections.</span></span>|  
|<span data-ttu-id="e202c-157">"WMI"</span><span class="sxs-lookup"><span data-stu-id="e202c-157">"WMI"</span></span>|<span data-ttu-id="e202c-158">Microsoft WMI(Windows Management Instrumentation) 연결용 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="e202c-158">Connection manager for Microsoft Windows Management Instrumentation (WMI) connections.</span></span>|  
  
 <span data-ttu-id="e202c-159">다음 코드 예에서는 <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A>의 <xref:Microsoft.SqlServer.Dts.Runtime.Package> 컬렉션에 OLE DB 및 FILE 연결을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-159">The following code example demonstrates adding an OLE DB and FILE connection to the <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> collection of a <xref:Microsoft.SqlServer.Dts.Runtime.Package>.</span></span> <span data-ttu-id="e202c-160">그런 다음 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e202c-160">The example then sets the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> properties.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      // Create a package, and retrieve its connections.  
      Package pkg = new Package();  
      Connections pkgConns = pkg.Connections;  
  
      // Add an OLE DB connection to the package, using the   
      // method defined in the AddConnection class.  
      CreateConnection myOLEDBConn = new CreateConnection();  
      myOLEDBConn.CreateOLEDBConnection(pkg);  
  
      // View the new connection in the package.  
      Console.WriteLine("Connection description: {0}",  
         pkg.Connections["SSIS Connection Manager for OLE DB"].Description);  
  
      // Add a second connection to the package.  
      CreateConnection myFileConn = new CreateConnection();  
      myFileConn.CreateFileConnection(pkg);  
  
      // View the second connection in the package.  
      Console.WriteLine("Connection description: {0}",  
        pkg.Connections["SSIS Connection Manager for Files"].Description);  
  
      Console.WriteLine();  
      Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count);  
  
      Console.Read();  
    }  
  }  
  // <summary>  
  // This class contains the definitions for multiple  
  // connection managers.  
  // </summary>  
  public class CreateConnection  
  {  
    // Private data.  
    private ConnectionManager ConMgr;  
  
    // Class definition for OLE DB Provider.  
    public void CreateOLEDBConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("OLEDB");  
      ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" +  
        "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" +  
        "Data Source=(local);";  
      ConMgr.Name = "SSIS Connection Manager for OLE DB";  
      ConMgr.Description = "OLE DB connection to the AdventureWorks database.";  
    }  
    public void CreateFileConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("File");  
      ConMgr.ConnectionString = @"\\<yourserver>\<yourfolder>\books.xml";  
      ConMgr.Name = "SSIS Connection Manager for Files";  
      ConMgr.Description = "Flat File connection";  
    }  
  }  
  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    ' Create a package, and retrieve its connections.  
    Dim pkg As New Package()  
    Dim pkgConns As Connections = pkg.Connections  
  
    ' Add an OLE DB connection to the package, using the   
    ' method defined in the AddConnection class.  
    Dim myOLEDBConn As New CreateConnection()  
    myOLEDBConn.CreateOLEDBConnection(pkg)  
  
    ' View the new connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for OLE DB").Description)  
  
    ' Add a second connection to the package.  
    Dim myFileConn As New CreateConnection()  
    myFileConn.CreateFileConnection(pkg)  
  
    ' View the second connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for Files").Description)  
  
    Console.WriteLine()  
    Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
' This class contains the definitions for multiple  
' connection managers.  
  
Public Class CreateConnection  
  ' Private data.  
  Private ConMgr As ConnectionManager  
  
  ' Class definition for OLE DB provider.  
  Public Sub CreateOLEDBConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("OLEDB")  
    ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" & _  
      "Data Source=(local);"  
    ConMgr.Name = "SSIS Connection Manager for OLE DB"  
    ConMgr.Description = "OLE DB connection to the AdventureWorks database."  
  End Sub  
  
  Public Sub CreateFileConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("File")  
    ConMgr.ConnectionString = "\\<yourserver>\<yourfolder>\books.xml"  
    ConMgr.Name = "SSIS Connection Manager for Files"  
    ConMgr.Description = "Flat File connection"  
  End Sub  
  
End Class  
```  
  
 <span data-ttu-id="e202c-161">**샘플 출력:**</span><span class="sxs-lookup"><span data-stu-id="e202c-161">**Sample Output:**</span></span>  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Number of connections in package: 2`  
  
## <a name="external-resources"></a><span data-ttu-id="e202c-162">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="e202c-162">External Resources</span></span>  
 <span data-ttu-id="e202c-163">carlprothman.net의 기술 문서 - [Connection Strings](https://go.microsoft.com/fwlink/?LinkId=220743)</span><span class="sxs-lookup"><span data-stu-id="e202c-163">Technical article, [Connection Strings](https://go.microsoft.com/fwlink/?LinkId=220743), on carlprothman.net.</span></span>  
  
<span data-ttu-id="e202c-164">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e202c-164">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e202c-165">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e202c-165">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e202c-166">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="e202c-166">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e202c-167">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="e202c-167">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e202c-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e202c-168">See Also</span></span>  
 <span data-ttu-id="e202c-169">[SSIS&#41; 연결을 &#40;Integration Services](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="e202c-169">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="e202c-170">연결 관리자 만들기</span><span class="sxs-lookup"><span data-stu-id="e202c-170">Create Connection Managers</span></span>](../create-connection-managers.md)  
  
  
