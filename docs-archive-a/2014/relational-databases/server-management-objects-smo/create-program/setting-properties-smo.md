---
title: 설정 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: de381f8e4e9dfe9f6590638742e988f866ccabdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735176"
---
# <a name="setting-properties"></a><span data-ttu-id="fecaf-102">속성 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-102">Setting Properties</span></span>
  <span data-ttu-id="fecaf-103">속성은 개체에 대한 설명 정보를 저장하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-103">Properties are values that store descriptive information about the object.</span></span> <span data-ttu-id="fecaf-104">예를 들어 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구성 옵션은 <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> 개체의 속성으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-104">For example, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration options are represented by the <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> object's properties.</span></span> <span data-ttu-id="fecaf-105">속성 컬렉션을 사용하여 직접 또는 간접적으로 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-105">Properties can be accessed either directly or indirectly by using the property collection.</span></span> <span data-ttu-id="fecaf-106">속성에 직접 액세스하는 경우 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-106">Accessing properties directly uses the following syntax:</span></span>  
  
 `objInstance.PropertyName`  
  
 <span data-ttu-id="fecaf-107">속성에 읽기/쓰기 권한 또는 읽기 전용 권한이 있는지에 따라 속성 값을 수정하거나 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-107">A property value can be modified or retrieved depending on whether the property has read/write access or read-only access.</span></span> <span data-ttu-id="fecaf-108">또한 특정 속성을 설정해야 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-108">It is also necessary to set certain properties before an object can be created.</span></span> <span data-ttu-id="fecaf-109">자세한 내용은 특정 개체에 대한 SMO 참조를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fecaf-109">For more information, see the SMO reference for the particular object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fecaf-110">자식 개체의 컬렉션은 개체의 속성으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-110">Collections of child objects appear as the property of an object.</span></span> <span data-ttu-id="fecaf-111">예를 들어 `Tables` 컬렉션은 `Server` 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-111">For example, the `Tables` collection is a property of a `Server` object.</span></span> <span data-ttu-id="fecaf-112">자세한 내용은 [Using Collections](using-collections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fecaf-112">For more information, see [Using Collections](using-collections.md).</span></span>  
  
 <span data-ttu-id="fecaf-113">개체의 속성은 속성 컬렉션의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-113">The properties of an object are members of the Properties collection.</span></span> <span data-ttu-id="fecaf-114">속성 컬렉션을 사용하여 개체의 모든 속성을 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-114">The Properties collection can be used to iterate through every property of an object.</span></span>  
  
 <span data-ttu-id="fecaf-115">다음과 같은 이유로 속성을 사용할 수 없는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-115">Sometimes a property is not available for the following reasons:</span></span>  
  
-   <span data-ttu-id="fecaf-116">이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서 새로운 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]기능을 나타내는 속성에 액세스하려는 경우와 같이 서버 버전에서 속성을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-116">The server version does not support the property, such as if you try to access a property that represents a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] feature on an older version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="fecaf-117">설치되지 않은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구성 요소를 나타내는 속성에 액세스하려는 경우와 같이 서버에서 속성 데이터를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-117">The server does not provide data for the property, such as if you try to access a property that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component that is not installed.</span></span>  
  
 <span data-ttu-id="fecaf-118"><xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> 및 <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO 실행을 catch하여 이러한 문제를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-118">You can handle these circumstances by catching the <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> and the <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException> SMO exceptions.</span></span>  
  
## <a name="setting-default-initialization-fields"></a><span data-ttu-id="fecaf-119">기본 초기화 필드 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-119">Setting Default Initialization Fields</span></span>  
 <span data-ttu-id="fecaf-120">SMO는 개체를 검색할 때 최적화를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-120">SMO performs an optimization when retrieving objects.</span></span> <span data-ttu-id="fecaf-121">최적화는 다음과 같은 상태를 자동으로 조정하여 로드되는 속성 수를 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-121">The optimization minimizes the number of properties loaded by automatically scaling between the following states:</span></span>  
  
1.  <span data-ttu-id="fecaf-122">부분적으로 로드됨.</span><span class="sxs-lookup"><span data-stu-id="fecaf-122">Partially loaded.</span></span> <span data-ttu-id="fecaf-123">개체를 처음 참조하는 경우 이름 및 스키마와 같은 최소한의 속성만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-123">When an object is first referenced it has a minimum of properties available (such as Name and Schema).</span></span>  
  
2.  <span data-ttu-id="fecaf-124">전체 로드됨.</span><span class="sxs-lookup"><span data-stu-id="fecaf-124">Fully loaded.</span></span> <span data-ttu-id="fecaf-125">아무 속성이나 참조하면 나머지 속성이 신속하게 로드되어 초기화되고 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-125">When any property is referenced, the remaining properties that are quick to load, are initialized and are made available.</span></span>  
  
3.  <span data-ttu-id="fecaf-126">많은 메모리를 사용하는 속성.</span><span class="sxs-lookup"><span data-stu-id="fecaf-126">Properties that use lots of memory.</span></span> <span data-ttu-id="fecaf-127">사용할 수 없는 나머지 속성은 많은 메모리를 사용하며 <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> 속성 값이 true입니다(예: <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>).</span><span class="sxs-lookup"><span data-stu-id="fecaf-127">The remaining unavailable properties use lots of memory and have an <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> property value of true (such as <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>).</span></span> <span data-ttu-id="fecaf-128">이러한 속성은 구체적으로 참조될 때만 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-128">These properties are loaded only when specifically referenced.</span></span>  
  
 <span data-ttu-id="fecaf-129">애플리케이션이 부분적으로 로드됨 상태에서 제공되는 속성 이외의 추가 속성을 인출하는 경우 쿼리를 제출하여 이러한 추가 속성을 검색하고 전체 로드됨 상태로 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-129">If your application does fetch extra properties, besides the ones provided in the partially loaded state, it submits a query to retrieve these extra properties and scales up to the fully loaded state.</span></span> <span data-ttu-id="fecaf-130">이로 인해 클라이언트와 서버 간에 불필요한 트래픽이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-130">This can cause unnecessary traffic between the client and server.</span></span> <span data-ttu-id="fecaf-131"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 메서드를 호출하여 보다 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-131">More optimization can be achieved by calling the <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method.</span></span> <span data-ttu-id="fecaf-132"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 메서드를 사용하면 개체를 초기화할 때 로드되는 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-132">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method allows specification of the properties that are loaded when the object is initialized.</span></span>  
  
 <span data-ttu-id="fecaf-133"><xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> 메서드는 다시 설정될 때까지 또는 나머지 애플리케이션에 대해 속성 로드 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-133">The <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> method sets the property loading behavior for the rest of application or until it is reset.</span></span> <span data-ttu-id="fecaf-134"><xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> 메서드를 사용하여 원래 동작을 저장하고 필요한 경우 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-134">You can save the original behavior by using the <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> method and restore it as required.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fecaf-135">예</span><span class="sxs-lookup"><span data-stu-id="fecaf-135">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a><span data-ttu-id="fecaf-136">Visual Basic에서 속성 가져오기 및 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-136">Getting and Setting a Property in Visual Basic</span></span>  
 <span data-ttu-id="fecaf-137">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Information> 속성을 가져오는 방법과 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> 속성의 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 속성을 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 열거 유형의 `ExecuteSql` 멤버로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-137">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a><span data-ttu-id="fecaf-138">Visual C#에서 속성 가져오기 및 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-138">Getting and Setting a Property in Visual C#</span></span>  
 <span data-ttu-id="fecaf-139">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Information> 속성을 가져오는 방법과 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> 속성의 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 속성을 <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> 열거 유형의 `ExecuteSql` 멤버로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-139">This code example shows how to get the <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Information> object and how to set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property to the `ExecuteSql` member of the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> enumerated type.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a><span data-ttu-id="fecaf-140">Visual Basic에서 개체를 만들기 전에 다양한 속성 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-140">Setting Various Properties Before an Object is Created in Visual Basic</span></span>  
 <span data-ttu-id="fecaf-141">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Table> 속성을 직접 설정하는 방법과 <xref:Microsoft.SqlServer.Management.Smo.Table> 개체를 만들기 전에 열을 만들고 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-141">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a><span data-ttu-id="fecaf-142">Visual C#에서 개체를 만들기 전에 다양한 속성 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-142">Setting Various Properties Before an Object is Created in Visual C#</span></span>  
 <span data-ttu-id="fecaf-143">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.Table> 속성을 직접 설정하는 방법과 <xref:Microsoft.SqlServer.Management.Smo.Table> 개체를 만들기 전에 열을 만들고 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-143">This code example shows how to directly set the <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Table> object, and how to create and add columns before you create the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a><span data-ttu-id="fecaf-144">Visual Basic에서 개체의 모든 속성 반복</span><span class="sxs-lookup"><span data-stu-id="fecaf-144">Iterating Through All Properties of an Object in Visual Basic</span></span>  
 <span data-ttu-id="fecaf-145">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 개체의 `Properties` 컬렉션을 반복하고 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 출력 화면에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-145">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
 <span data-ttu-id="fecaf-146">이 예에서 <xref:Microsoft.SqlServer.Management.Smo.Property> 개체는 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 키워드이기도 하기 때문에 대괄호 안에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-146">In the example, the <xref:Microsoft.SqlServer.Management.Smo.Property> object has been put in square parentheses because it is also a [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a><span data-ttu-id="fecaf-147">Visual C#에서 개체의 모든 속성 반복</span><span class="sxs-lookup"><span data-stu-id="fecaf-147">Iterating Through All Properties of an Object in Visual C#</span></span>  
 <span data-ttu-id="fecaf-148">이 코드 예제에서는 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 개체의 `Properties` 컬렉션을 반복하고 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 출력 화면에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-148">This code example iterates through the `Properties` collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object and displays them on the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Output screen.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a><span data-ttu-id="fecaf-149">Visual Basic에서 기본 초기화 필드 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-149">Setting Default Initialization Fields in Visual Basic</span></span>  
 <span data-ttu-id="fecaf-150">이 코드 예제에서는 SMO 프로그램에서 초기화되는 개체 속성 수를 최소화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-150">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="fecaf-151"><xref:System.Collections.Specialized.StringCollection> 개체를 사용하려면 `using System.Collections.Specialized` 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-151">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]<span data-ttu-id="fecaf-152">를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스로 전송되는 문 수와 이 최적화를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-152">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a><span data-ttu-id="fecaf-153">Visual C#에서 기본 초기화 필드 설정</span><span class="sxs-lookup"><span data-stu-id="fecaf-153">Setting Default Initialization Fields in Visual C#</span></span>  
 <span data-ttu-id="fecaf-154">이 코드 예제에서는 SMO 프로그램에서 초기화되는 개체 속성 수를 최소화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-154">This code example shows how to minimize the number of object properties initialized in an SMO program.</span></span> <span data-ttu-id="fecaf-155"><xref:System.Collections.Specialized.StringCollection> 개체를 사용하려면 `using System.Collections.Specialized` 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-155">You have to include the `using System.Collections.Specialized`; statement to use the <xref:System.Collections.Specialized.StringCollection> object.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]<span data-ttu-id="fecaf-156">를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스로 전송되는 문 수와 이 최적화를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fecaf-156">can be used to compare the number statements sent to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with this optimization.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  
