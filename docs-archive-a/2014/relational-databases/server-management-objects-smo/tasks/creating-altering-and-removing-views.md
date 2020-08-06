---
title: 뷰 생성, 변경 및 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd8d75e413b1871ce4b8784f5087cb08ed08da73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660445"
---
# <a name="creating-altering-and-removing-views"></a><span data-ttu-id="404d9-102">뷰 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="404d9-102">Creating, Altering, and Removing Views</span></span>
  <span data-ttu-id="404d9-103">SMO([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects)에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 뷰는 <xref:Microsoft.SqlServer.Management.Smo.View> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] views are represented by the <xref:Microsoft.SqlServer.Management.Smo.View> object.</span></span>  
  
 <span data-ttu-id="404d9-104"><xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.View> 속성이 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-104">The <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.View> object defines the view.</span></span> <span data-ttu-id="404d9-105">이 속성은 뷰를 만드는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 문에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-105">It is the equivalent of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statement for creating a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="404d9-106">예제</span><span class="sxs-lookup"><span data-stu-id="404d9-106">Example</span></span>  
 <span data-ttu-id="404d9-107">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="404d9-108">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="404d9-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a><span data-ttu-id="404d9-109">Visual Basic에서 뷰 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="404d9-109">Creating, Altering, and Removing a View in Visual Basic</span></span>  
 <span data-ttu-id="404d9-110">이 코드 예제는 내부 조인을 사용하여 두 테이블을 조인한 뷰를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-110">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="404d9-111">텍스트 모드를 사용하여 뷰를 작성하므로 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-111">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a><span data-ttu-id="404d9-112">Visual C#에서 뷰 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="404d9-112">Creating, Altering, and Removing a View in Visual C#</span></span>  
 <span data-ttu-id="404d9-113">이 코드 예제는 내부 조인을 사용하여 두 테이블을 조인한 뷰를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-113">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="404d9-114">텍스트 모드를 사용하여 뷰를 작성하므로 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-114">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```csharp
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a><span data-ttu-id="404d9-115">PowerShell에서 뷰 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="404d9-115">Creating, Altering, and Removing a View in PowerShell</span></span>  
 <span data-ttu-id="404d9-116">이 코드 예제는 내부 조인을 사용하여 두 테이블을 조인한 뷰를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-116">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="404d9-117">텍스트 모드를 사용하여 뷰를 작성하므로 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="404d9-117">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View -argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.
$myview.Create()  
  
# Remove the view
$myview.Drop();  
```  
  
## <a name="see-also"></a><span data-ttu-id="404d9-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="404d9-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
