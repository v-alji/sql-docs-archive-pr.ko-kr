---
title: 통계 만들기 및 업데이트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- statistical information [SMO]
ms.assetid: 47a0a172-a969-4deb-bca9-dd04401a0fe1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c61bb1b213e4b57c7fbae0b0ec7294c9401a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660444"
---
# <a name="creating-and-updating-statistics"></a><span data-ttu-id="8217a-102">통계 생성 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="8217a-102">Creating and Updating Statistics</span></span>
  <span data-ttu-id="8217a-103">SMO에서 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 개체를 사용하여 데이터베이스의 쿼리 처리에 대한 통계 정보를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-103">In SMO, statistical information about processing queries in the database can be collected by using the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object.</span></span>  
  
 <span data-ttu-id="8217a-104"><xref:Microsoft.SqlServer.Management.Smo.Statistic> 및 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 개체를 사용하여 임의 열에 대한 통계를 만드는 것도 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-104">It is possible to create statistics for any column by using the <xref:Microsoft.SqlServer.Management.Smo.Statistic> and <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object.</span></span> <span data-ttu-id="8217a-105"><xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> 개체에서 통계를 업데이트하려면 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 메서드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-105">The <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> method can be run to update the statistics in the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object.</span></span> <span data-ttu-id="8217a-106">결과는 쿼리 최적화 프로그램에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-106">The results can be viewed in the Query Optimizer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8217a-107">예제</span><span class="sxs-lookup"><span data-stu-id="8217a-107">Example</span></span>  
 <span data-ttu-id="8217a-108">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-108">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="8217a-109">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8217a-109">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-and-update-statistics-in-visual-basic"></a><span data-ttu-id="8217a-110">Visual Basic에서 통계 생성 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="8217a-110">Creating and Update Statistics in Visual Basic</span></span>  
 <span data-ttu-id="8217a-111">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 개체가 만들어지는 기존 데이터베이스에 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-111">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStatistics1](SMO How to#SMO_VBStatistics1)]  -->  
  
## <a name="creating-and-update-statistics-in-visual-c"></a><span data-ttu-id="8217a-112">Visual C#에서 통계 생성 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="8217a-112">Creating and Update Statistics in Visual C#</span></span>  
 <span data-ttu-id="8217a-113">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 개체가 만들어지는 기존 데이터베이스에 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-113">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Reference the CreditCard table.   
  
           Table tb = db.Tables["CreditCard", "Sales"];  
            //Define a Statistic object by supplying the parent table and name   
            //arguments in the constructor.   
            Statistic stat = default(Statistic);  
            stat = new Statistic(tb, "Test_Statistics");  
            //Define a StatisticColumn object variable for the CardType column   
            //and add to the Statistic object variable.   
            StatisticColumn statcol = default(StatisticColumn);  
            statcol = new StatisticColumn(stat, "CardType");  
            stat.StatisticColumns.Add(statcol);  
            //Create the statistic counter on the instance of SQL Server.   
            stat.Create();  
        }  
```  
  
## <a name="creating-and-update-statistics-in-powershell"></a><span data-ttu-id="8217a-114">PowerShell에서 통계 생성 및 업데이트</span><span class="sxs-lookup"><span data-stu-id="8217a-114">Creating and Update Statistics in PowerShell</span></span>  
 <span data-ttu-id="8217a-115">이 코드 예제는 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 개체 및 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 개체가 만들어지는 기존 데이터베이스에 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8217a-115">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
CD AdventureWorks2012\tables  
  
#Get a reference to the table  
$tb = get-item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -argumentlist $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -argumentlist $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index   
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -argumentlist $fti, "Name"  
  
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
