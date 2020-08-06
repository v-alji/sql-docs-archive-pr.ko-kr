---
title: 호출 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13216b4c533527d4249471073580d7c86f6b07e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735179"
---
# <a name="calling-methods"></a><span data-ttu-id="efc89-102">메서드 호출</span><span class="sxs-lookup"><span data-stu-id="efc89-102">Calling Methods</span></span>
  <span data-ttu-id="efc89-103">메서드는 `Checkpoint` 데이터베이스에서을 실행 하거나 인스턴스에 대해 열거 된 로그온 목록을 요청 하는 등 개체와 관련 된 특정 태스크를 수행 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-103">Methods perform specific tasks related to the object, such as issuing a `Checkpoint` on a database or requesting an enumerated list of logons for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="efc89-104">메서드는 개체에 대해 작업을 수행하며</span><span class="sxs-lookup"><span data-stu-id="efc89-104">Methods perform an operation on an object.</span></span> <span data-ttu-id="efc89-105">매개 변수를 사용할 수 있고 반환 값을 갖는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-105">Methods can take parameters and often have a return value.</span></span> <span data-ttu-id="efc89-106">반환 값은 단순한 데이터 형식, 복잡한 개체 또는 여러 멤버가 포함된 구조일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-106">The return value can be a simple data type, a complex object, or a structure that contains many members.</span></span>  
  
 <span data-ttu-id="efc89-107">메서드가 성공적으로 실행되었는지 여부를 확인하려면 예외 처리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-107">Use exception handling to detect whether the method has been successful.</span></span> <span data-ttu-id="efc89-108">자세한 내용은 [Handling SMO Exceptions](handling-smo-exceptions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efc89-108">For more information, see [Handling SMO Exceptions](handling-smo-exceptions.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="efc89-109">예</span><span class="sxs-lookup"><span data-stu-id="efc89-109">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a><span data-ttu-id="efc89-110">Visual Basic에서 간단한 SMO 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="efc89-110">Using a Simple SMO Method in Visual Basic</span></span>  
 <span data-ttu-id="efc89-111">이 예에서 <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> 메서드는 매개 변수를 사용하지 않고 반환 값도 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-111">In this example, the <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> method takes no parameters and has no return value.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods1](SMO How to#SMO_VBMethods1)]  -->  
  
## <a name="using-a-simple-smo-method-in-visual-c"></a><span data-ttu-id="efc89-112">Visual C#에서 간단한 SMO 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="efc89-112">Using a Simple SMO Method in Visual C#</span></span>  
 <span data-ttu-id="efc89-113">이 예에서 <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> 메서드는 매개 변수를 사용하지 않고 반환 값도 가지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-113">In this example, the <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> method takes no parameters and has no return value.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 <span data-ttu-id="efc89-114">}</span><span class="sxs-lookup"><span data-stu-id="efc89-114">}</span></span>  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a><span data-ttu-id="efc89-115">Visual Basic에서 매개 변수가 있는 SMO 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="efc89-115">Using an SMO Method with a Parameter in Visual Basic</span></span>  
 <span data-ttu-id="efc89-116"><xref:Microsoft.SqlServer.Management.Smo.Table> 개체에는 <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>라는 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-116">The <xref:Microsoft.SqlServer.Management.Smo.Table> object has a method called <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>.</span></span> <span data-ttu-id="efc89-117">이 메서드에는 `FillFactor`를 지정하는 숫자 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-117">This method requires a numeric parameter that specifies the `FillFactor`.</span></span>  
  
```  
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a><span data-ttu-id="efc89-118">Visual C#에서 매개 변수가 있는 SMO 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="efc89-118">Using an SMO Method with a Parameter in Visual C#</span></span>  
 <span data-ttu-id="efc89-119"><xref:Microsoft.SqlServer.Management.Smo.Table> 개체에는 <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>라는 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-119">The <xref:Microsoft.SqlServer.Management.Smo.Table> object has a method called <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>.</span></span> <span data-ttu-id="efc89-120">이 메서드에는 `FillFactor`를 지정하는 숫자 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-120">This method requires a numeric parameter that specifies the `FillFactor`.</span></span>  
  
```  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a><span data-ttu-id="efc89-121">Visual Basic에서 DataTable 개체를 반환하는 열거형 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="efc89-121">Using an Enumeration Method that Returns a DataTable Object in Visual Basic</span></span>  
 <span data-ttu-id="efc89-122">이 섹션에서는 열거형 메서드를 호출하는 방법 및 반환된 <xref:System.Data.DataTable> 개체의 데이터를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-122">This section describes how to call an enumeration method and how to handle the data in the returned <xref:System.Data.DataTable> object.</span></span>  
  
 <span data-ttu-id="efc89-123"><xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> 메서드는 <xref:System.Data.DataTable> 개체를 반환하며, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 모든 데이터 정렬 정보에 액세스하려면 이 개체를 추가적으로 탐색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-123">The <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> method returns a <xref:System.Data.DataTable> object, which requires further navigation to access all available collation information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a><span data-ttu-id="efc89-124">Visual C#에서 DataTable 개체를 반환하는 열거형 메서드 사용</span><span class="sxs-lookup"><span data-stu-id="efc89-124">Using an Enumeration Method that Returns a DataTable Object in Visual C#</span></span>  
 <span data-ttu-id="efc89-125">이 섹션에서는 열거형 메서드를 호출하는 방법 및 반환된 <xref:System.Data.DataTable> 개체의 데이터를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-125">This section describes how to call an enumeration method and how to handle the data in the returned <xref:System.Data.DataTable> object.</span></span>  
  
 <span data-ttu-id="efc89-126"><xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> 메서드는 시스템 <xref:System.Data.DataTable> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-126">The <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> method returns a system <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="efc89-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 모든 데이터 정렬 정보에 액세스하려면 <xref:System.Data.DataTable> 개체를 추가적으로 탐색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-127">The <xref:System.Data.DataTable> object requires further navigation to access all available collation information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a><span data-ttu-id="efc89-128">Visual Basic에서 개체 생성</span><span class="sxs-lookup"><span data-stu-id="efc89-128">Constructing an Object in Visual Basic</span></span>  
 <span data-ttu-id="efc89-129">`New` 연산자를 사용하여 모든 개체의 생성자를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-129">The constructor of any object can be called by using the `New` operator.</span></span> <span data-ttu-id="efc89-130"><xref:Microsoft.SqlServer.Management.Smo.Database> 개체 생성자는 오버로드되며 예제에 사용된 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체 생성자의 버전은 매개 변수 두 개, 즉 데이터베이스가 속해 있는 부모 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체와 새 데이터베이스의 이름을 나타내는 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-130">The <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor is overloaded and the version of the <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor that is used in the sample takes two parameters: the parent <xref:Microsoft.SqlServer.Management.Smo.Server> object to which the database belongs, and a string that represents the name of the new database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods4](SMO How to#SMO_VBMethods4)]  -->  
  
## <a name="constructing-an-object-in-visual-c"></a><span data-ttu-id="efc89-131">Visual C#에서 개체 생성</span><span class="sxs-lookup"><span data-stu-id="efc89-131">Constructing an Object in Visual C#</span></span>  
 <span data-ttu-id="efc89-132">`New` 연산자를 사용하여 모든 개체의 생성자를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-132">The constructor of any object can be called by using the `New` operator.</span></span> <span data-ttu-id="efc89-133"><xref:Microsoft.SqlServer.Management.Smo.Database> 개체 생성자는 오버로드되며 예제에 사용된 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체 생성자의 버전은 매개 변수 두 개, 즉 데이터베이스가 속해 있는 부모 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체와 새 데이터베이스의 이름을 나타내는 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-133">The <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor is overloaded and the version of the <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor that is used in the sample takes two parameters: the parent <xref:Microsoft.SqlServer.Management.Smo.Server> object to which the database belongs, and a string that represents the name of the new database.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a><span data-ttu-id="efc89-134">Visual Basic에서 SMO 개체 복사</span><span class="sxs-lookup"><span data-stu-id="efc89-134">Copying an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="efc89-135">이 코드 예에서는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 메서드를 사용하여 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-135">This code example uses the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to create a copy of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="efc89-136"><xref:Microsoft.SqlServer.Management.Smo.Server> 개체는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-136">The <xref:Microsoft.SqlServer.Management.Smo.Server> object represents a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VCMethods6](SMO How to#SMO_VCMethods6)]  -->  
  
## <a name="copying-an-smo-object-in-visual-c"></a><span data-ttu-id="efc89-137">Visual C#에서 SMO 개체 복사</span><span class="sxs-lookup"><span data-stu-id="efc89-137">Copying an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="efc89-138">이 코드 예에서는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 메서드를 사용하여 <xref:Microsoft.SqlServer.Management.Smo.Server> 개체의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-138">This code example uses the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to create a copy of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="efc89-139"><xref:Microsoft.SqlServer.Management.Smo.Server> 개체는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-139">The <xref:Microsoft.SqlServer.Management.Smo.Server> object represents a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a><span data-ttu-id="efc89-140">Visual Basic에서 서버 프로세스 모니터링</span><span class="sxs-lookup"><span data-stu-id="efc89-140">Monitoring Server Processes in Visual Basic</span></span>  
 <span data-ttu-id="efc89-141">열거형 메서드를 사용하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스에 대한 현재 상태 형식 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-141">You can obtain the current status type information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through enumeration methods.</span></span> <span data-ttu-id="efc89-142">코드 예에서는 <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> 메서드를 사용하여 현재 프로세스에 대한 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-142">The code example uses the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> method to discover information about the current processes.</span></span> <span data-ttu-id="efc89-143">또한 이 예에서는 반환된 <xref:System.Data.DataTable> 개체의 열과 행으로 작업하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-143">It also demonstrates how to work with the columns and rows in the returned <xref:System.Data.DataTable> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods5](SMO How to#SMO_VBMethods5)]  -->  
  
## <a name="monitoring-server-processes-in-visual-c"></a><span data-ttu-id="efc89-144">Visual C#에서 서버 프로세스 모니터링</span><span class="sxs-lookup"><span data-stu-id="efc89-144">Monitoring Server Processes in Visual C#</span></span>  
 <span data-ttu-id="efc89-145">열거형 메서드를 사용하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스에 대한 현재 상태 형식 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-145">You can obtain the current status type information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through enumeration methods.</span></span> <span data-ttu-id="efc89-146">코드 예에서는 <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> 메서드를 사용하여 현재 프로세스에 대한 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-146">The code example uses the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> method to discover information about the current processes.</span></span> <span data-ttu-id="efc89-147">또한 이 예에서는 반환된 <xref:System.Data.DataTable> 개체의 열과 행으로 작업하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="efc89-147">It also demonstrates how to work with the columns and rows in the returned <xref:System.Data.DataTable> object.</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a><span data-ttu-id="efc89-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efc89-148">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
