---
title: 사용자, 역할 및 로그인 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
ms.openlocfilehash: bb53e7b4a5748e46c7cb147e1cda50652d8b8805
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653246"
---
# <a name="managing-users-roles-and-logins"></a><span data-ttu-id="f50a4-102">사용자, 역할 및 로그인 관리</span><span class="sxs-lookup"><span data-stu-id="f50a4-102">Managing Users, Roles, and Logins</span></span>
  <span data-ttu-id="f50a4-103">SMO에서 로그인은 <xref:Microsoft.SqlServer.Management.Smo.Login> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-103">In SMO, logins are represented by the <xref:Microsoft.SqlServer.Management.Smo.Login> object.</span></span> <span data-ttu-id="f50a4-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로그온이 있으면 서버 역할에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-104">When the logon exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it can be added to a server role.</span></span> <span data-ttu-id="f50a4-105">서버 역할은 <xref:Microsoft.SqlServer.Management.Smo.ServerRole> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-105">The server role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ServerRole> object.</span></span> <span data-ttu-id="f50a4-106">데이터베이스 역할은 <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> 개체로 표시되고 애플리케이션 역할은 <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-106">The database role is represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> object and the application role is represented by the <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> object.</span></span>  
  
 <span data-ttu-id="f50a4-107">서버 수준과 연관된 권한은 <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> 개체의 속성으로 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-107">Privileges associated with the server level are listed as properties of the <xref:Microsoft.SqlServer.Management.Smo.ServerPermission> object.</span></span> <span data-ttu-id="f50a4-108">개별 로그온 계정에 대해 서버 수준 권한을 부여, 거부 또는 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-108">The server level privileges can be granted to, denied to, or revoked from individual logon accounts.</span></span>  
  
 <span data-ttu-id="f50a4-109">모든 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체에는 데이터베이스의 모든 사용자를 지정하는 <xref:Microsoft.SqlServer.Management.Smo.UserCollection> 개체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-109">Every <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.UserCollection> object that specifies all users in the database.</span></span> <span data-ttu-id="f50a4-110">각 사용자는 로그온과 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-110">Each user is associated with a logon.</span></span> <span data-ttu-id="f50a4-111">하나의 로그온은 둘 이상의 데이터베이스의 사용자들과 연관될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-111">One logon can be associated with users in more than one database.</span></span> <span data-ttu-id="f50a4-112"><xref:Microsoft.SqlServer.Management.Smo.Login> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 메서드를 사용하여 로그온과 연관된 모든 데이터베이스의 사용자를 모두 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-112">The <xref:Microsoft.SqlServer.Management.Smo.Login> object's <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method can be used to list all users in every database that is associated with the logon.</span></span> <span data-ttu-id="f50a4-113">또는 <xref:Microsoft.SqlServer.Management.Smo.User> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Login> 속성이 사용자와 연관되어 있는 로그온을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-113">Alternatively, the <xref:Microsoft.SqlServer.Management.Smo.User> object's <xref:Microsoft.SqlServer.Management.Smo.Login> property specifies the logon that is associated with the user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f50a4-114">데이터베이스는 사용자가 특정 태스크를 수행할 수 있는 일련의 데이터베이스 수준 권한을 지정하는 역할도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-114">databases also have roles that specify a set of database level privileges that let a user perform specific tasks.</span></span> <span data-ttu-id="f50a4-115">서버 역할과 달리 데이터베이스 역할은 고정되지 않아서</span><span class="sxs-lookup"><span data-stu-id="f50a4-115">Unlike server roles, database roles are not fixed.</span></span> <span data-ttu-id="f50a4-116">생성, 수정 및 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-116">They can be created, modified, and removed.</span></span> <span data-ttu-id="f50a4-117">대량 관리를 위해 데이터베이스 역할에 권한 및 사용자를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-117">Privileges and users can be assigned to a database role for bulk administration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50a4-118">예제</span><span class="sxs-lookup"><span data-stu-id="f50a4-118">Example</span></span>  
 <span data-ttu-id="f50a4-119">다음 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-119">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="f50a4-120">자세한 내용은 visual studio [.net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 visual [Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f50a4-120">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a><span data-ttu-id="f50a4-121">Visual Basic에서 로그인 및 연관된 사용자 열거</span><span class="sxs-lookup"><span data-stu-id="f50a4-121">Enumerating Logins and Associated Users in Visual Basic</span></span>  
 <span data-ttu-id="f50a4-122">데이터베이스의 모든 사용자는 로그온과 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-122">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="f50a4-123">로그온은 둘 이상의 데이터베이스의 사용자들과 연관될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-123">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="f50a4-124">코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Login> 메서드를 호출하여 로그온과 연관된 데이터베이스 사용자를 모두 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-124">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="f50a4-125">이 예에서는 열거할 매핑 정보가 있는지 확인하기 위해 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 로그온과 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-125">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a><span data-ttu-id="f50a4-126">Visual C#에서 로그인 및 연관된 사용자 열거</span><span class="sxs-lookup"><span data-stu-id="f50a4-126">Enumerating Logins and Associated Users in Visual C#</span></span>  
 <span data-ttu-id="f50a4-127">데이터베이스의 모든 사용자는 로그온과 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-127">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="f50a4-128">로그온은 둘 이상의 데이터베이스의 사용자들과 연관될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-128">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="f50a4-129">코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Login> 메서드를 호출하여 로그온과 연관된 데이터베이스 사용자를 모두 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-129">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="f50a4-130">이 예에서는 열거할 매핑 정보가 있는지 확인하기 위해 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 로그온과 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-130">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```csharp
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a><span data-ttu-id="f50a4-131">PowerShell에서 로그인 및 연관된 사용자 열거</span><span class="sxs-lookup"><span data-stu-id="f50a4-131">Enumerating Logins and Associated Users in PowerShell</span></span>  
 <span data-ttu-id="f50a4-132">데이터베이스의 모든 사용자는 로그온과 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-132">Every user in a database is associated with a logon.</span></span> <span data-ttu-id="f50a4-133">로그온은 둘 이상의 데이터베이스의 사용자들과 연관될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-133">The logon can be associated with users in more than one database.</span></span> <span data-ttu-id="f50a4-134">코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Login> 메서드를 호출하여 로그온과 연관된 데이터베이스 사용자를 모두 나열하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-134">The code example shows how to call the <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Login> object to list all the database users who are associated with the logon.</span></span> <span data-ttu-id="f50a4-135">이 예에서는 열거할 매핑 정보가 있는지 확인하기 위해 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 로그온과 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-135">The example creates a logon and user in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database to make sure there is mapping information to enumerate.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database object  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a><span data-ttu-id="f50a4-136">역할 및 사용자 관리</span><span class="sxs-lookup"><span data-stu-id="f50a4-136">Managing Roles and Users</span></span>  
 <span data-ttu-id="f50a4-137">이 예제에서는 역할 및 사용자를 관리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-137">This sample demonstrates how to how to manage roles and users.</span></span> <span data-ttu-id="f50a4-138">첫 번째 예제에서는 C#를 사용하고 두 번째 쿼리에서는 Visual Basic을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-138">The first sample uses C#, the second Visual Basic.</span></span> <span data-ttu-id="f50a4-139">이 예제는 다음 어셈블리를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-139">These samples need to reference the following assemblies:</span></span>  
  
-   <span data-ttu-id="f50a4-140">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="f50a4-140">Microsoft.SqlServer.Smo.dll</span></span>  
  
-   <span data-ttu-id="f50a4-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="f50a4-141">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
-   <span data-ttu-id="f50a4-142">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="f50a4-142">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
-   <span data-ttu-id="f50a4-143">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="f50a4-143">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
```csharp
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```  
  
 <span data-ttu-id="f50a4-144">Visual Basic 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="f50a4-144">This is the Visual Basic version:</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
