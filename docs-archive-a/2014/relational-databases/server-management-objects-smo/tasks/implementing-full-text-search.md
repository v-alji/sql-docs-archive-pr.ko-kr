---
title: 전체 텍스트 검색 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8b797e2a38c9136c34b7058b539fca522e03229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728159"
---
# <a name="implementing-full-text-search"></a><span data-ttu-id="17926-102">전체 텍스트 검색 구현</span><span class="sxs-lookup"><span data-stu-id="17926-102">Implementing Full-Text Search</span></span>
  <span data-ttu-id="17926-103">전체 텍스트 검색은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스별로 사용할 수 있으며 SMO에서 <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17926-103">Full-text search is available per instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and is represented in SMO by the <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> object.</span></span> <span data-ttu-id="17926-104"><xref:Microsoft.SqlServer.Management.Smo.FullTextService> 개체는 `Server` 개체 아래에 있으며,</span><span class="sxs-lookup"><span data-stu-id="17926-104">The <xref:Microsoft.SqlServer.Management.Smo.FullTextService> object resides under the `Server` object.</span></span> <span data-ttu-id="17926-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 전체 텍스트 검색 서비스의 구성 옵션을 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="17926-105">It is used to manage the configuration options for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Full Text Search service.</span></span> <span data-ttu-id="17926-106"><xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> 개체에 속하는 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체는 데이터베이스에 정의된 전체 텍스트 카탈로그를 나타내는 <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> 개체 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="17926-106">The <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> object belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object and it is a collection of <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> objects that represent full-text catalogs defined for the database.</span></span> <span data-ttu-id="17926-107">일반 인덱스와 달리 전체 텍스트 인덱스는 각 테이블에 하나만 정의할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="17926-107">You can only have one full-text index defined for each table, unlike normal indexes.</span></span> <span data-ttu-id="17926-108"><xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> 개체에서 <xref:Microsoft.SqlServer.Management.Smo.Table> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17926-108">This is represented by a <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object in the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="17926-109">전체 텍스트 검색 서비스를 만들려면 데이터베이스에 전체 텍스트 카탈로그를 정의하고 데이터베이스의 테이블 중 하나에 전체 텍스트 검색 인덱스를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17926-109">To create a full-text search service, you must have a full-text catalog defined on the database and a full-text search index defined on one of the tables in the database.</span></span>  
  
 <span data-ttu-id="17926-110">먼저, <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> 생성자를 호출하고 카탈로그 이름을 지정하여 데이터베이스에 전체 텍스트 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-110">First, create a full-text catalog on the database by calling the <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> constructor and specifying the catalog name.</span></span> <span data-ttu-id="17926-111">그런 다음 생성자를 호출하고 저장할 테이블을 지정하여 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-111">Then, create the full-text index by calling the constructor and specifying the table on which it is to be created.</span></span> <span data-ttu-id="17926-112">그리고 나서 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> 개체를 사용하여 테이블의 열 이름을 지정하면 전체 텍스트 인덱스에 대한 인덱스 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17926-112">You can then add index columns for the full-text index, by using the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object and providing the name of the column within the table.</span></span> <span data-ttu-id="17926-113">그런 다음 생성한 카탈로그에 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17926-113">Then, set the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> property to the catalog you have created.</span></span> <span data-ttu-id="17926-114">마지막으로, <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> 메서드를 호출하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 전체 텍스트 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-114">Finally, call the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> method and create the full-text index on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="17926-115">예제</span><span class="sxs-lookup"><span data-stu-id="17926-115">Example</span></span>  
 <span data-ttu-id="17926-116">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17926-116">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="17926-117">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17926-117">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a><span data-ttu-id="17926-118">Visual Basic에서 전체 텍스트 검색 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="17926-118">Creating a Full-Text Search Service in Visual Basic</span></span>  
 <span data-ttu-id="17926-119">이 코드 예제에서는 `ProductCategory` 예제 데이터베이스의 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 테이블에 대한 전체 텍스트 검색 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-119">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="17926-120">그런 다음 `ProductCategory` 테이블의 이름 열에 전체 텍스트 검색 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-120">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="17926-121">전체 텍스트 검색 인덱스를 사용하려면 해당 열에 이미 고유 인덱스가 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17926-121">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a><span data-ttu-id="17926-122">Visual C#에서 전체 텍스트 검색 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="17926-122">Creating a Full-Text Search Service in Visual C#</span></span>  
 <span data-ttu-id="17926-123">이 코드 예제에서는 `ProductCategory` 예제 데이터베이스의 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 테이블에 대한 전체 텍스트 검색 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-123">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="17926-124">그런 다음 `ProductCategory` 테이블의 이름 열에 전체 텍스트 검색 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-124">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="17926-125">전체 텍스트 검색 인덱스를 사용하려면 해당 열에 이미 고유 인덱스가 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17926-125">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a><span data-ttu-id="17926-126">PowerShell에서 전체 텍스트 검색 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="17926-126">Creating a Full-Text Search Service in PowerShell</span></span>  
 <span data-ttu-id="17926-127">이 코드 예제에서는 `ProductCategory` 예제 데이터베이스의 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 테이블에 대한 전체 텍스트 검색 카탈로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-127">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="17926-128">그런 다음 `ProductCategory` 테이블의 이름 열에 전체 텍스트 검색 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17926-128">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="17926-129">전체 텍스트 검색 인덱스를 사용하려면 해당 열에 이미 고유 인덱스가 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17926-129">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = Get-Item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = Get-Item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -ArgumentList $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -ArgumentList $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -ArgumentList $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
