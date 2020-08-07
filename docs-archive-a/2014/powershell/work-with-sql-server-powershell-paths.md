---
title: SQL Server PowerShell 경로 작업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d2647251eb1c8843d4ab7a95d2c439e47f5bb6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731772"
---
# <a name="work-with-sql-server-powershell-paths"></a><span data-ttu-id="ab5da-102">SQL Server PowerShell 경로 작업</span><span class="sxs-lookup"><span data-stu-id="ab5da-102">Work With SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="ab5da-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] 공급자 경로의 노드로 이동한 후에는 노드에 연결된 [!INCLUDE[ssDE](../includes/ssde-md.md)] 관리 개체에서 메서드 및 속성을 사용하여 작업을 수행하거나 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-103">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform work or retrieve information by using the methods and properties from the [!INCLUDE[ssDE](../includes/ssde-md.md)] management object associated with the node.</span></span>  
  
1.  [<span data-ttu-id="ab5da-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ab5da-104">Before You Begin</span></span>](#BeforeYouBegin)  
  
2.  <span data-ttu-id="ab5da-105">**경로 노드에서 작업하려면**  [메서드 및 속성 나열](#ListPropMeth), [메서드 및 속성 사용](#UsePropMeth)</span><span class="sxs-lookup"><span data-stu-id="ab5da-105">**To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab5da-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ab5da-106">Before You Begin</span></span>  
 <span data-ttu-id="ab5da-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] 공급자 경로의 노드로 이동한 후에는 다음 두 가지 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-107">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform two types of actions:</span></span>  
  
-   <span data-ttu-id="ab5da-108">**Rename-Item**과 같이 노드에서 작동하는 Windows PowerShell cmdlet을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-108">You can run Windows PowerShell cmdlets that operate on nodes, such as **Rename-Item**.</span></span>  
  
-   <span data-ttu-id="ab5da-109">SMO와 같은 관련 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 관리 개체 모델에서 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-109">You can call the methods from the associated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] management object model, such as SMO.</span></span> <span data-ttu-id="ab5da-110">예를 들어 경로에서 Databases 노드로 이동하는 경우 <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스의 메서드와 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-110">For example, if you navigate to the Databases node in a path, you can use the methods and properties of the <xref:Microsoft.SqlServer.Management.Smo.Database> class.</span></span>  
  
 <span data-ttu-id="ab5da-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 [!INCLUDE[ssDE](../includes/ssde-md.md)]인스턴스의 개체를 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-111">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider is used to manage the objects in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="ab5da-112">데이터베이스의 데이터 작업에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-112">It is not used to work with the data in databases.</span></span> <span data-ttu-id="ab5da-113">테이블 또는 뷰로 이동한 경우에는 공급자를 사용하여 데이터에 대한 선택, 삽입, 업데이트 또는 삭제 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-113">If you have navigated to a table or view, you cannot use the provider to select, insert, update, or delete data.</span></span> <span data-ttu-id="ab5da-114">Windows PowerShell 환경에서 테이블 및 뷰의 데이터를 쿼리하거나 변경하려면 **Invoke-Sqlcmd** cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="ab5da-114">Use the **Invoke-Sqlcmd** cmdlet to query or change data in tables and views from the Windows PowerShell environment.</span></span> <span data-ttu-id="ab5da-115">자세한 내용은 [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ab5da-115">For more information, see [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md).</span></span>  
  
##  <a name="listing-methods-and-properties"></a><a name="ListPropMeth"></a><span data-ttu-id="ab5da-116">메서드 및 속성 나열</span><span class="sxs-lookup"><span data-stu-id="ab5da-116">Listing Methods and Properties</span></span>
  
 <span data-ttu-id="ab5da-117">특정 개체 또는 개체 클래스에 사용할 수 있는 메서드 및 속성을 보려면 **Get-Member** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-117">To view the methods and properties available for specific objects or object classes, use the **Get-Member** cmdlet.</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="ab5da-118">예: 메서드 및 속성 나열</span><span class="sxs-lookup"><span data-stu-id="ab5da-118">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="ab5da-119">이 예에서는 Windows PowerShell 변수를 SMO <xref:Microsoft.SqlServer.Management.Smo.Database> 클래스로 설정하고 메서드 및 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-119">This example sets a Windows PowerShell variable to the SMO <xref:Microsoft.SqlServer.Management.Smo.Database> class and lists the methods and properties:</span></span>  
  
```powershell
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member -Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="ab5da-120">또한 **Get-Member** 를 사용하여 Windows PowerShell 경로의 끝 노드와 관련된 메서드 및 속성을 나열할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-120">You can also use **Get-Member** to list the methods and properties that are associated with the end node of a Windows PowerShell path.</span></span>  
  
 <span data-ttu-id="ab5da-121">이 예에서는 SQLSERVER: 경로의 Databases 노드로 이동하고 컬렉션 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-121">This example navigates to the Databases node in a SQLSERVER: path and lists the collection properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="ab5da-122">이 예에서는 SQLSERVER: 경로의 AdventureWorks2012 노드로 이동하고 개체 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-122">This example navigates to the AdventureWorks2012 node in a SQLSERVER: path and lists the object properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="using-smo-methods-and-properties"></a><a name="UsePropMeth"></a><span data-ttu-id="ab5da-123">SMO 메서드 및 속성 사용</span><span class="sxs-lookup"><span data-stu-id="ab5da-123">Using SMO Methods and Properties</span></span>  
  
 <span data-ttu-id="ab5da-124">[!INCLUDE[ssDE](../includes/ssde-md.md)] 공급자 경로에서 개체에 대한 작업을 수행하려면 SMO 메서드 및 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-124">To perform work on objects from a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can use SMO methods and properties.</span></span>  
  
### <a name="examples-using-methods-and-properties"></a><span data-ttu-id="ab5da-125">예: 메서드 및 속성 사용</span><span class="sxs-lookup"><span data-stu-id="ab5da-125">Examples: Using Methods and Properties</span></span>  
 <span data-ttu-id="ab5da-126">이 예에서는 SMO **Schema** 속성을 사용하여 AdventureWorks2012의 Sales 스키마에서 테이블 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-126">This example uses the SMO **Schema** property to get a list of the tables from the Sales schema in AdventureWorks2012:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | Where {$_.Schema -eq "Sales"}  
```  
  
 <span data-ttu-id="ab5da-127">이 예에서는 SMO **script** 메서드를 사용 하 여 `CREATE VIEW` AdventureWorks2012에서 뷰를 다시 만드는 데 필요한 문이 포함 된 스크립트를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-127">This example uses the SMO **Script** method to generate a script that contains the `CREATE VIEW` statements you must have to re-create the views in AdventureWorks2012:</span></span>  
  
```powershell
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 <span data-ttu-id="ab5da-128">이 예에서는 SMO **Create** 메서드를 사용하여 데이터베이스를 만든 다음 **State** 속성을 사용하여 데이터베이스의 유무를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ab5da-128">This example uses the SMO **Create** method to create a database, and then uses the **State** property to show whether the database exists:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab5da-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab5da-129">See Also</span></span>  
 <span data-ttu-id="ab5da-130">[SQL Server PowerShell 공급자](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="ab5da-130">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="ab5da-131">[SQL Server PowerShell 경로 탐색](navigate-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="ab5da-131">[Navigate SQL Server PowerShell Paths](navigate-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="ab5da-132">[Urn를 SQL Server 공급자 경로로 변환](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="ab5da-132">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="ab5da-133">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab5da-133">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
