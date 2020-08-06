---
title: 권한 부여, 취소 및 거부 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- granting permissions [SMO]
- denying permissions [SMO]
- permissions [SMO]
- revoking permissions [SMO]
ms.assetid: b0eb0f60-3e56-4880-b645-138832b38a1e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 059d9f6d4426f12de175654bdb196484d470c92f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728163"
---
# <a name="granting-revoking-and-denying-permissions"></a><span data-ttu-id="61a59-102">권한 부여, 취소 및 거부</span><span class="sxs-lookup"><span data-stu-id="61a59-102">Granting, Revoking, and Denying Permissions</span></span>
  <span data-ttu-id="61a59-103"><xref:Microsoft.SqlServer.Management.Smo.ServerPermission> 개체는 일련의 권한 또는 개별 서버 권한을 <xref:Microsoft.SqlServer.Management.Smo.ServerPermissionSet> 개체에 할당하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-103">The <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> object is used to assign a set of permissions or an individual server permission to the <xref:Microsoft.SqlServer.Management.Smo.ServerPermissionSet> object.</span></span> <span data-ttu-id="61a59-104">서버 수준 권한의 경우 피부여자가 로그온을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-104">For server level permissions, the grantee refers to a logon.</span></span> <span data-ttu-id="61a59-105">Windows에 의해 인증된 로그온이 Windows 사용자 이름으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-105">Logons authenticated by Windows are listed as Windows user names.</span></span> <span data-ttu-id="61a59-106">이 코드 예제를 실행하면 피부여자로부터 권한이 취소되고 <xref:Microsoft.SqlServer.Management.Smo.Server.EnumServerPermissions%2A> 메서드로 권한이 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-106">When this code sample runs, it revokes the permission from the grantee and verifies it has been removed with the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumServerPermissions%2A> method.</span></span>  
  
 <span data-ttu-id="61a59-107"><xref:Microsoft.SqlServer.Management.Smo.DatabasePermissionSet> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.ObjectPermissionSet> 개체를 사용하여 비슷한 방법으로 데이터베이스 권한 및 데이터베이스 개체 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-107">Database permissions and database object permissions can be assigned similarly by using the <xref:Microsoft.SqlServer.Management.Smo.DatabasePermissionSet> object and the <xref:Microsoft.SqlServer.Management.Smo.ObjectPermissionSet> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a59-108">예제</span><span class="sxs-lookup"><span data-stu-id="61a59-108">Example</span></span>  
 <span data-ttu-id="61a59-109">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-109">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="61a59-110">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="61a59-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="granting-server-permissions-in-visual-basic"></a><span data-ttu-id="61a59-111">Visual Basic에서 서버 권한 부여</span><span class="sxs-lookup"><span data-stu-id="61a59-111">Granting Server Permissions in Visual Basic</span></span>  
 <span data-ttu-id="61a59-112">이 코드 예제는 지정된 로그인에 Create Endpoint 및 Alter Any Endpoint 권한을 부여한 다음, 권한을 열거하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-112">This code example grants the Create Endpoint and Alter Any Endpoint permissions to the specified login, and then enumerates and displays the permissions.</span></span> <span data-ttu-id="61a59-113">권한 중 하나를 취소하고 나서 권한을 다시 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-113">One of the permissions is revoked, and then the permissions are enumerated again.</span></span> <span data-ttu-id="61a59-114">이 예에서는 지정된 로그인에 지정된 시작 권한이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-114">This example assumes that the specified login has the specified permissions to start with.</span></span>  
  
```vb
' compile with: /r:Microsoft.SqlServer.Smo.dll /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll /r:Microsoft.SqlServer.SqlEnum.dll  
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
  
      ' Creating the logins (Grantee)  
      Dim vGrantee As [String] = "Grantee1"  
      Dim login As New Login(svr, vGrantee)  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim vGrantee2 As [String] = "Grantee2"  
      Dim login2 As New Login(svr, vGrantee2)  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@2")  
  
      ' Define a ServerPermissionSet that contains permission to Create Endpoint and Alter Any Endpoint.   
      Dim sps As New ServerPermissionSet(ServerPermission.CreateEndpoint)  
      sps.Add(ServerPermission.AlterAnyEndpoint)  
  
      ' Grant Create Endpoint and Alter Any Endpoint permissions to Grantee  
      svr.Grant(sps, vGrantee)  
      svr.Grant(sps, vGrantee2)  
  
      ' Enumerate and display the server permissions in the set for the grantee specified in the vGrantee string variable.   
      Dim spis As ServerPermissionInfo() = svr.EnumServerPermissions(vGrantee, sps)  
      'enumerates all server permissions for the Grantee from the specified permission set  
      Console.WriteLine("====Before revoke===========")  
      For Each spi As ServerPermissionInfo In spis  
         Console.WriteLine(spi.Grantee + " has " & spi.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
  
      ' Revoke the create endpoint permission from the grantee.   
      svr.Revoke(New ServerPermissionSet(ServerPermission.CreateEndpoint), vGrantee)  
  
      ' Enumerate and display the server permissions in the set for the grantee specified in the vGrantee string variable.   
      spis = svr.EnumServerPermissions(vGrantee, sps)  
  
      Console.WriteLine("==After revoke=========")  
      For Each spi As ServerPermissionInfo In spis  
         Console.WriteLine(spi.Grantee + " has " & spi.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
  
      ' Grant the Create Server Role permission to the grantee.   
      svr.Grant(New ServerPermissionSet(ServerPermission.ViewAnyDatabase), vGrantee)  
      ' Enumerate and display the server permissions for the grantee specified in the vGrantee string variable.   
  
      ' enumerates all server permissions for the Grantee  
      spis = svr.EnumServerPermissions(vGrantee)  
  
      Console.WriteLine("==After grant========")  
  
      For Each spi As ServerPermissionInfo In spis  
         Console.WriteLine(spi.Grantee + " has " & spi.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine("")  
  
      ' Enumerate and display the server permissions in the set for all logins.   
      spis = svr.EnumServerPermissions(sps)  
      'enumerates all server permissions in the set for all logins  
      Console.WriteLine("==After grant========")  
  
      For Each spi As ServerPermissionInfo In spis  
         Console.WriteLine(spi.Grantee + " has " & spi.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine("")  
   End Sub  
End Class  
```  
  
## <a name="granting-server-permissions-in-visual-c"></a><span data-ttu-id="61a59-115">Visual C#에서 서버 권한 부여</span><span class="sxs-lookup"><span data-stu-id="61a59-115">Granting Server Permissions in Visual C#</span></span>  
 <span data-ttu-id="61a59-116">이 코드 예제는 지정된 로그인에 Create Endpoint 및 Alter Any Endpoint 권한을 부여한 다음, 권한을 열거하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-116">This code example grants the Create Endpoint and Alter Any Endpoint permissions to the specified login, and then enumerates and displays the permissions.</span></span> <span data-ttu-id="61a59-117">권한 중 하나를 취소하고 나서 권한을 다시 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-117">One of the permissions is revoked, and then the permissions are enumerated again.</span></span> <span data-ttu-id="61a59-118">이 예에서는 지정된 로그인에 지정된 시작 권한이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-118">This example assumes that the specified login has the specified permissions to start with.</span></span>  
  
```csharp
// compile with: /r:Microsoft.SqlServer.Smo.dll /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll /r:Microsoft.SqlServer.SqlEnum.dll  
using System;  
using Microsoft.SqlServer.Management.Smo;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
  
      // Creating the logins (Grantee)  
      String vGrantee = "Grantee1";  
      Login login = new Login(svr, vGrantee);  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      String vGrantee2 = "Grantee2";  
      Login login2 = new Login(svr, vGrantee2);  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@2");  
  
      // Define a ServerPermissionSet that contains permission to Create Endpoint and Alter Any Endpoint.   
      ServerPermissionSet sps = new ServerPermissionSet(ServerPermission.CreateEndpoint);  
      sps.Add(ServerPermission.AlterAnyEndpoint);  
  
      // Grant Create Endpoint and Alter Any Endpoint permissions to Grantee  
      svr.Grant(sps, vGrantee);  
      svr.Grant(sps, vGrantee2);  
  
      // Enumerate and display the server permissions in the set for the grantee specified in the vGrantee string variable.   
      ServerPermissionInfo[] spis = svr.EnumServerPermissions(vGrantee, sps); //enumerates all server permissions for the Grantee from the specified permission set  
  
      Console.WriteLine("====Before revoke===========");  
      foreach (ServerPermissionInfo spi in spis) {  
         Console.WriteLine(spi.Grantee + " has " + spi.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
  
      // Revoke the create endpoint permission from the grantee.   
      svr.Revoke(new ServerPermissionSet(ServerPermission.CreateEndpoint), vGrantee);  
  
      // Enumerate and display the server permissions in the set for the grantee specified in the vGrantee string variable.   
      spis = svr.EnumServerPermissions(vGrantee, sps);  
  
      Console.WriteLine("==After revoke=========");  
      foreach (ServerPermissionInfo spi in spis) {  
         Console.WriteLine(spi.Grantee + " has " + spi.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
  
      // Grant the Create Server Role permission to the grantee.   
      svr.Grant(new ServerPermissionSet(ServerPermission.ViewAnyDatabase), vGrantee);  
      // Enumerate and display the server permissions for the grantee specified in the vGrantee string variable.   
  
      // enumerates all server permissions for the Grantee  
      spis = svr.EnumServerPermissions(vGrantee);   
  
      Console.WriteLine("==After grant========");  
  
      foreach (ServerPermissionInfo spi in spis) {  
         Console.WriteLine(spi.Grantee + " has " + spi.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine("");  
  
      // Enumerate and display the server permissions in the set for all logins.   
      spis = svr.EnumServerPermissions(sps); //enumerates all server permissions in the set for all logins  
  
      Console.WriteLine("==After grant========");  
  
      foreach (ServerPermissionInfo spi in spis) {  
         Console.WriteLine(spi.Grantee + " has " + spi.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine("");  
   }  
}  
```  
  
## <a name="granting-server-permissions-in-powershell"></a><span data-ttu-id="61a59-119">PowerShell에서 서버 권한 부여</span><span class="sxs-lookup"><span data-stu-id="61a59-119">Granting Server Permissions in PowerShell</span></span>  
 <span data-ttu-id="61a59-120">이 코드 예제는 지정된 로그인에 Create Endpoint 및 Alter Any Endpoint 권한을 부여한 다음, 권한을 열거하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-120">This code example grants the Create Endpoint and Alter Any Endpoint permissions to the specified login, and then enumerates and displays the permissions.</span></span> <span data-ttu-id="61a59-121">권한 중 하나를 취소하고 나서 권한을 다시 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-121">One of the permissions is revoked, and then the permissions are enumerated again.</span></span> <span data-ttu-id="61a59-122">이 예에서는 지정된 로그인에 지정된 시작 권한이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="61a59-122">This example assumes that the specified login has the specified permissions to start with.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#The subject login:  
# "Place Login Name here - has permission to Create Endpoints"  
$vGrantee = "LoginName"  
  
#This sample assumes that the grantee already has permission to Create Endpoints.   
  
$sps  =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.ServerPermissionSet  
  
$sps.CreateEndpoint = $true  
$sps.AlterAnyEndpoint = $true  
  
#This sample assumes that the grantee already has permission to Create Endpoints.   
  
#Enumerate and display the server permissions in the set for the grantee specified  
# in the vGrantee string variable.  
$spis = $srv.EnumServerPermissions($vGrantee)  
  
"===Before revoke============="  
foreach ( $spi in $spis)  
{  
    $spi.Grantee + " has " + $spi.PermissionType + " permission."  
}  
""  
#remove perission to create an endpoint  
$sps.CreateEndpoint = $false  
$srv.Revoke($sps, $vGrantee)  
  
#Enumerate and display the server permissions in the set for the grantee specified  
# in the vGrantee string variable.  
$spis = $srv.EnumServerPermissions($vGrantee)  
  
"===After revoke============="  
foreach ( $spi in $spis)  
{  
    $spi.Grantee + " has " + $spi.PermissionType + " permission."  
}  
""  
#Grant the revoked permissions back  
$sps.CreateEndpoint = $true  
$sps.AlterAnyEndpoint = $true  
$srv.Grant($sps, $vGrantee)  
  
#Enumerate and display the server permissions in the set for the grantee specified  
# in the vGrantee string variable.  
$spis = $srv.EnumServerPermissions($vGrantee)  
  
"===After grant============="  
foreach ( $spi in $spis)  
{  
    $spi.Grantee + " has " + $spi.PermissionType + " permission."  
}  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="61a59-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61a59-123">See Also</span></span>  
 [<span data-ttu-id="61a59-124">사용 권한 계층&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="61a59-124">Permissions Hierarchy &#40;Database Engine&#41;</span></span>](../../security/permissions-hierarchy-database-engine.md)  
