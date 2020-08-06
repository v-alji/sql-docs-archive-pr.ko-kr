---
title: 스크립팅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- dependencies [SMO]
- scripts [SMO]
ms.assetid: 13a35511-3987-426b-a3b7-3b2e83900dc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf46798597de021976cefa943a17500e773f9274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732492"
---
# <a name="scripting"></a><span data-ttu-id="63139-102">스크립팅</span><span class="sxs-lookup"><span data-stu-id="63139-102">Scripting</span></span>
  <span data-ttu-id="63139-103">SMO의 스크립팅은 <xref:Microsoft.SqlServer.Management.Smo.Scripter> 개체와 자식 개체, 또는 개별 개체의 `Script` 메서드로 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="63139-103">Scripting in SMO is controlled by the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects, or the `Script` method on individual objects.</span></span> <span data-ttu-id="63139-104"><xref:Microsoft.SqlServer.Management.Smo.Scripter>개체는 인스턴스의 개체에 대 한 종속성 관계의 매핑을 제어 합니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="63139-104">The <xref:Microsoft.SqlServer.Management.Smo.Scripter> object controls the mapping out of dependency relationships for objects on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="63139-105"><xref:Microsoft.SqlServer.Management.Smo.Scripter> 개체와 자식 개체를 사용한 고급 스크립팅은 다음 3단계 프로세스를 거칩니다.</span><span class="sxs-lookup"><span data-stu-id="63139-105">Advanced scripting by using the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects is a three phase process:</span></span>  
  
1.  <span data-ttu-id="63139-106">검색</span><span class="sxs-lookup"><span data-stu-id="63139-106">Discovery</span></span>  
  
2.  <span data-ttu-id="63139-107">목록 생성</span><span class="sxs-lookup"><span data-stu-id="63139-107">List generation</span></span>  
  
3.  <span data-ttu-id="63139-108">스크립트 생성</span><span class="sxs-lookup"><span data-stu-id="63139-108">Script generation</span></span>  
  
 <span data-ttu-id="63139-109">검색 단계에서는 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> 개체를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="63139-109">The discovery phase uses the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object.</span></span> <span data-ttu-id="63139-110">개체의 URN 목록을 제공하면 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> 메서드가 URN 목록의 개체에 대해 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="63139-110">Given an URN list of objects, the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object returns a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object for the objects in the URN list.</span></span> <span data-ttu-id="63139-111">부울 *Fparents* 매개 변수는 지정 된 개체의 부모 또는 자식을 검색할지 여부를 선택 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63139-111">The Boolean *fParents* parameter is used to select whether the parents or the children of the specified object are to be discovered.</span></span> <span data-ttu-id="63139-112">이 단계에서 종속성 트리를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63139-112">The dependency tree can be modified at this stage.</span></span>  
  
 <span data-ttu-id="63139-113">목록 생성 단계에서는 트리가 전달되고 결과 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="63139-113">In the list generation phase, the tree is passed in and the resulting list is returned.</span></span> <span data-ttu-id="63139-114">이 개체 목록은 스크립팅 순서로 나열되며 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63139-114">This object list is in scripting order and can be manipulated.</span></span>  
  
 <span data-ttu-id="63139-115">목록 생성 단계에서는 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> 메서드를 사용하여 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="63139-115">The list generation phases use the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> method to return a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>.</span></span> <span data-ttu-id="63139-116">이 단계에서 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63139-116">The <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> can be modified at this stage.</span></span>  
  
 <span data-ttu-id="63139-117">마지막 세 번째 단계에서는 지정된 목록 및 스크립팅 옵션으로 스크립트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="63139-117">In the third and final phase, a script is generated with the specified list and scripting options.</span></span> <span data-ttu-id="63139-118">결과가 <xref:System.Collections.Specialized.StringCollection> 시스템 개체로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="63139-118">The result is returned as a <xref:System.Collections.Specialized.StringCollection> system object.</span></span> <span data-ttu-id="63139-119">이 단계에서는 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> 개체의 항목 컬렉션과 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> 및 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>와 같은 속성으로부터 종속 개체 이름이 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="63139-119">In this phase the dependent object names are then extracted from the Items collection of the <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object and properties such as <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> and <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63139-120">예제</span><span class="sxs-lookup"><span data-stu-id="63139-120">Example</span></span>  
 <span data-ttu-id="63139-121">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63139-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="63139-122">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63139-122">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="63139-123">이 코드 예제에는 System.Collections.Specialized 네임스페이스에 대한 `Imports` 문이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="63139-123">This code example requires an `Imports` statement for the System.Collections.Specialized namespace.</span></span> <span data-ttu-id="63139-124">애플리케이션의 선언 앞에 다른 Imports 문과 함께 삽입하십시오.</span><span class="sxs-lookup"><span data-stu-id="63139-124">Insert this with the other Imports statements, before any declarations in the application.</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-basic"></a><span data-ttu-id="63139-125">Visual Basic에서 데이터베이스의 종속성 스크립팅</span><span class="sxs-lookup"><span data-stu-id="63139-125">Scripting Out the Dependencies for a Database in Visual Basic</span></span>  
 <span data-ttu-id="63139-126">이 코드 예제는 종속성을 검색하고 목록 전체를 반복하여 결과를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63139-126">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
  
Public Class A  
   Public Shared Sub Main()  
      ' database name  
      Dim dbName As [String] = "AdventureWorksLT2012"   ' database name  
  
      ' Connect to the local, default instance of SQL Server.   
      Dim srv As New Server()  
  
      ' Reference the database.    
      Dim db As Database = srv.Databases(dbName)  
  
      ' Define a Scripter object and set the required scripting options.   
      Dim scrp As New Scripter(srv)  
      scrp.Options.ScriptDrops = False  
      scrp.Options.WithDependencies = True  
      scrp.Options.Indexes = True   ' To include indexes  
      scrp.Options.DriAllConstraints = True   ' to include referential constraints in the script  
  
      ' Iterate through the tables in database and script each one. Display the script.  
      For Each tb As Table In db.Tables  
         ' check if the table is not a system table  
         If tb.IsSystemObject = False Then  
            Console.WriteLine("-- Scripting for table " + tb.Name)  
  
            ' Generating script for table tb  
            Dim sc As System.Collections.Specialized.StringCollection = scrp.Script(New Urn() {tb.Urn})  
            For Each st As String In sc  
               Console.WriteLine(st)  
            Next  
            Console.WriteLine("--")  
         End If  
      Next  
   End Sub  
End Class  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-c"></a><span data-ttu-id="63139-127">Visual C#에서 데이터베이스의 종속성 스크립팅</span><span class="sxs-lookup"><span data-stu-id="63139-127">Scripting Out the Dependencies for a Database in Visual C#</span></span>  
 <span data-ttu-id="63139-128">이 코드 예제는 종속성을 검색하고 목록 전체를 반복하여 결과를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63139-128">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
  
public class A {  
   public static void Main() {   
      String dbName = "AdventureWorksLT2012"; // database name  
  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the database.    
      Database db = srv.Databases[dbName];  
  
      // Define a Scripter object and set the required scripting options.   
      Scripter scrp = new Scripter(srv);  
      scrp.Options.ScriptDrops = false;  
      scrp.Options.WithDependencies = true;  
      scrp.Options.Indexes = true;   // To include indexes  
      scrp.Options.DriAllConstraints = true;   // to include referential constraints in the script  
  
      // Iterate through the tables in database and script each one. Display the script.     
      foreach (Table tb in db.Tables) {   
         // check if the table is not a system table  
         if (tb.IsSystemObject == false) {  
            Console.WriteLine("-- Scripting for table " + tb.Name);  
  
            // Generating script for table tb  
            System.Collections.Specialized.StringCollection sc = scrp.Script(new Urn[]{tb.Urn});  
            foreach (string st in sc) {  
               Console.WriteLine(st);  
            }  
            Console.WriteLine("--");  
         }  
      }   
   }  
}  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-powershell"></a><span data-ttu-id="63139-129">PowerShell에서 데이터베이스의 종속성 스크립팅</span><span class="sxs-lookup"><span data-stu-id="63139-129">Scripting Out the Dependencies for a Database in PowerShell</span></span>  
 <span data-ttu-id="63139-130">이 코드 예제는 종속성을 검색하고 목록 전체를 반복하여 결과를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63139-130">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
# Create a Scripter object and set the required scripting options.  
$scrp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Scripter -ArgumentList (Get-Item .)  
$scrp.Options.ScriptDrops = $false  
$scrp.Options.WithDependencies = $true  
$scrp.Options.IncludeIfNotExists = $true  
  
# Set the path context to the tables in AdventureWorks2012.  
CD Databases\AdventureWorks2012\Tables  
  
foreach ($Item in Get-ChildItem)  
 {    
 $scrp.Script($Item)  
 }  
```  
