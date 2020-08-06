---
title: 컬렉션 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: stevestein
ms.author: sstein
ms.openlocfilehash: 288f2110952a85d2aab610c0f1da40d433882400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647552"
---
# <a name="using-collections"></a><span data-ttu-id="c8396-102">컬렉션 사용</span><span class="sxs-lookup"><span data-stu-id="c8396-102">Using Collections</span></span>
  <span data-ttu-id="c8396-103">컬렉션은 동일한 개체 클래스에서 구성되고 동일한 부모 개체를 공유하는 개체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-103">A collection is a list of objects that have been constructed from the same object class and that share the same parent object.</span></span> <span data-ttu-id="c8396-104">컬렉션 개체에는 항상 Collection 접미사가 있는 개체 유형의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-104">The collection object always contains the name of the object type with the Collection suffix.</span></span> <span data-ttu-id="c8396-105">예를 들어 지정한 테이블의 열에 액세스하려면 <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> 개체 유형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-105">For example, to access the columns in a specified table, use the <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> object type.</span></span> <span data-ttu-id="c8396-106">이 개체 유형에는 동일한 <xref:Microsoft.SqlServer.Management.Smo.Column> 개체에 속하는 모든 <xref:Microsoft.SqlServer.Management.Smo.Table> 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-106">It contains all the <xref:Microsoft.SqlServer.Management.Smo.Column> objects that belong to the same <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="c8396-107">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` 문 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` 문을 사용 하 여 컬렉션의 각 멤버를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-107">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` statement or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` statement can be used to iterate through each member of the collection.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c8396-108">예</span><span class="sxs-lookup"><span data-stu-id="c8396-108">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a><span data-ttu-id="c8396-109">Visual Basic에서 컬렉션을 사용하여 개체 참조</span><span class="sxs-lookup"><span data-stu-id="c8396-109">Referencing an Object by Using a Collection in Visual Basic</span></span>  
 <span data-ttu-id="c8396-110">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 및 <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> 속성을 사용하여 열 속성을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-110">This code example shows how to set a column property by using the <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, and <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> properties.</span></span> <span data-ttu-id="c8396-111">이러한 속성은 개체의 이름을 지정하는 매개 변수와 함께 사용될 때 특정 개체를 식별하는 데 사용할 수 있는 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-111">These properties represent collections, which can be used to identify a particular object when they are used with a parameter that specifies the name of the object.</span></span> <span data-ttu-id="c8396-112"><xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 컬렉션 개체 속성에는 이름과 스키마가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-112">The name and the schema are required for the <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> collection object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections1](SMO How to#SMO_VBCollections1)]  -->  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a><span data-ttu-id="c8396-113">Visual C#에서 컬렉션을 사용하여 개체 참조</span><span class="sxs-lookup"><span data-stu-id="c8396-113">Referencing an Object by Using a Collection in Visual C#</span></span>  
 <span data-ttu-id="c8396-114">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 및 <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> 속성을 사용하여 열 속성을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-114">This code example shows how to set a column property by using the <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, and <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> properties.</span></span> <span data-ttu-id="c8396-115">이러한 속성은 개체의 이름을 지정하는 매개 변수와 함께 사용될 때 특정 개체를 식별하는 데 사용할 수 있는 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-115">These properties represent collections, which can be used to identify a particular object when they are used with a parameter that specifies the name of the object.</span></span> <span data-ttu-id="c8396-116"><xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 컬렉션 개체 속성에는 이름과 스키마가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-116">The name and the schema are required for the <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> collection object property.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a><span data-ttu-id="c8396-117">Visual Basic에서 컬렉션의 멤버 전체 반복</span><span class="sxs-lookup"><span data-stu-id="c8396-117">Iterating Through the Members of a Collection in Visual Basic</span></span>  
 <span data-ttu-id="c8396-118">이 코드 예제에서는 <xref:Microsoft.AnalysisServices.Server.Databases%2A> 컬렉션 속성 전체를 반복하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 모든 데이터베이스 연결을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-118">This code example iterates through the <xref:Microsoft.AnalysisServices.Server.Databases%2A> collection property and displays all database connections to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections2](SMO How to#SMO_VBCollections2)]  -->  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a><span data-ttu-id="c8396-119">Visual C#에서 컬렉션의 멤버 전체 반복</span><span class="sxs-lookup"><span data-stu-id="c8396-119">Iterating Through the Members of a Collection in Visual C#</span></span>  
 <span data-ttu-id="c8396-120">이 코드 예제에서는 <xref:Microsoft.AnalysisServices.Server.Databases%2A> 컬렉션 속성 전체를 반복하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 모든 데이터베이스 연결을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c8396-120">This code example iterates through the <xref:Microsoft.AnalysisServices.Server.Databases%2A> collection property and displays all database connections to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
