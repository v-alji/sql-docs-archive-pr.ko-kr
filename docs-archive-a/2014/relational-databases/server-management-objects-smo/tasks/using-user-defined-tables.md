---
title: 사용자 정의 테이블 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined tables [SQL Server]
ms.assetid: 620a4e1f-9678-4711-ae09-bcf7c9cae724
author: stevestein
ms.author: sstein
ms.openlocfilehash: 869bff26dc6801a6844e31b11322eb43515f3eac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741680"
---
# <a name="using-user-defined-tables"></a><span data-ttu-id="f0b70-102">사용자 정의 테이블 사용</span><span class="sxs-lookup"><span data-stu-id="f0b70-102">Using User-Defined Tables</span></span>
  <span data-ttu-id="f0b70-103">사용자 정의 테이블은 테이블 형식의 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-103">User-defined tables represent tabular information.</span></span> <span data-ttu-id="f0b70-104">이들은 테이블 형식 데이터를 저장 프로시저나 사용자 정의 함수로 전달할 때 매개 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-104">They are used as parameters when you pass tabular data into stored procedures or user-defined functions.</span></span> <span data-ttu-id="f0b70-105">데이터베이스 테이블의 열 표시에는 사용자 정의 테이블을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-105">User-defined tables cannot be used to represent columns in a database table.</span></span>  
  
 <span data-ttu-id="f0b70-106"><xref:Microsoft.SqlServer.Management.Smo.Database> 개체에는 <xref:Microsoft.SqlServer.Management.Smo.Database.UserDefinedTableTypes%2A> 개체를 참조하는 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableTypeCollection> 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-106">The <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.Database.UserDefinedTableTypes%2A> property that references a <xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableTypeCollection> object.</span></span> <span data-ttu-id="f0b70-107"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType>해당 컬렉션의 각 개체에는 **Columns** <xref:Microsoft.SqlServer.Management.Smo.Column> 사용자 정의 테이블의 열을 나열 하는 개체의 컬렉션을 참조 하는 Columns 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-107">Each <xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType> object in that collection has a **Columns** property that refers to a collection of <xref:Microsoft.SqlServer.Management.Smo.Column> objects that list the columns in the user-defined table.</span></span> <span data-ttu-id="f0b70-108">사용자 정의 테이블에 열을 추가하려면 Add 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-108">Use the Add method to add columns to the user-defined table.</span></span>  
  
 <span data-ttu-id="f0b70-109"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType> 개체를 사용하여 새 사용자 정의 테이블을 정의할 때 여러 열과 이 열들 중 하나를 기반으로 하는 기본 키를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-109">When you define a new user-defined table by using the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType> object, you will have to supply columns and a primary key based on one of the columns.</span></span>  
  
 <span data-ttu-id="f0b70-110">사용자 정의 테이블 형식은 한번 만든 후 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-110">User-defined table types cannot be altered after they are created.</span></span> <span data-ttu-id="f0b70-111"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType>은 Alter 메서드를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-111">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedTableType> does not support the Alter method.</span></span> <span data-ttu-id="f0b70-112">사용자 정의 테이블 형식은 CHECK 제약 조건을 갖지만 형식을 수정할 수 없으므로 일부 확인 작업에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-112">User-defined table types can have check constraints, but some check operations will throw an exception because the type is not alterable.</span></span>  
  
 <span data-ttu-id="f0b70-113"><xref:Microsoft.SqlServer.Management.Smo.DataType> 클래스는 열 및 매개 변수와 연관된 데이터 형식을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-113">The <xref:Microsoft.SqlServer.Management.Smo.DataType> class is used to specify the data type that is associated with columns and parameters.</span></span> <span data-ttu-id="f0b70-114">사용자 정의 테이블 형식을 사용자 정의 함수 및 저장 프로시저에 대한 매개 변수로 지정하려면 이 형식을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f0b70-114">Use this type to specify the user-defined table type as a parameter for user-defined functions and stored procedures.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f0b70-115">예</span><span class="sxs-lookup"><span data-stu-id="f0b70-115">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-a-user-defined-table-in-visual-basic"></a><span data-ttu-id="f0b70-116">Visual Basic에서 사용자 정의 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="f0b70-116">Creating a User Defined Table in Visual Basic</span></span>  
 <span data-ttu-id="f0b70-117">이 예에서는 `StringCollection` 형식을 포함하는 클래스 라이브러리에 대해 imports 문을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-117">For this example, you will have to include an imports statement for the class library that contains the `StringCollection` type.</span></span>  
  
 `Imports System.Collections.Specialized`  
  
 <span data-ttu-id="f0b70-118">이 예는 사용자 정의 테이블을 만들어 사용자 정의 함수의 매개 변수로 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-118">The example demonstrates how to create a user-defined table, and then how to use it as a parameter in a user-defined function.</span></span>  
  
```vb
'Connect to the local, default instance of SQL Server  
        Dim srv As Server  
        srv = New Server  
        'Reference the AdventureWorks2012 database.  
        Dim db As Database  
        db = srv.Databases("AdventureWorks2012")  
        'Define a UserDefinedTableType object variable by supplying the 'database and name in the constructor.  
        Dim udtt As UserDefinedTableType  
        udtt = New UserDefinedTableType(db, "My_User_Defined_Table")  
        'Add three columns of different types to the  
        'UserDefinedTableType object.  
        udtt.Columns.Add(New Column(udtt, "Col1", DataType.Int))  
        udtt.Columns.Add(New Column(udtt, "Col2", DataType.VarCharMax))  
        udtt.Columns.Add(New Column(udtt, "Col3", DataType.Money))  
        'Define an Index object variable by supplying the user-defined  
        'table variable and name in the constructor.  
        Dim idx As Index  
        idx = New Index(udtt, "PK_UddtTable")  
        'Add the first column in the user-defined table as  
        'the indexed column.  
        idx.IndexedColumns.Add(New IndexedColumn(idx, "Col1"))  
        'Specify that the index is a clustered, unique, primary key.  
        idx.IsClustered = True  
        idx.IsUnique = True  
        idx.IndexKeyType = IndexKeyType.DriPrimaryKey  
        udtt.Indexes.Add(idx)  
        'Add the index and create the user-defined table.  
        udtt.Create()  
        'Display the Transact-SQL creation script for the  
        'user-defined table.  
        Dim sc As StringCollection  
        sc = udtt.Script()  
        For Each c As String In sc  
            Console.WriteLine(c)  
        Next  
  
        'Define a new user-defined function with a single parameter.  
        Dim udf As UserDefinedFunction  
        udf = New UserDefinedFunction(db, "My_User_Defined_Function")  
        udf.TextMode = False  
        udf.FunctionType = UserDefinedFunctionType.Scalar  
        udf.ImplementationType = ImplementationType.TransactSql  
        udf.DataType = DataType.DateTime  
        'Specify the parameter as a UserDefinedTableTable object.  
        Dim udfp As UserDefinedFunctionParameter  
        udfp = New UserDefinedFunctionParameter(udf, "@param")  
        udfp.DataType = New DataType(udtt)  
        udfp.IsReadOnly = True  
        udf.Parameters.Add(udfp)  
        'Specify the TextBody property to the Transact-SQL definition of the  
        'user-defined function.  
        udf.TextBody = "BEGIN RETURN (GETDATE());end"  
        'Create the user-defined function.  
        udf.Create()  
```  
  
## <a name="creating-a-user-defined-table-in-visual-c"></a><span data-ttu-id="f0b70-119">Visual C#에서 사용자 정의 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="f0b70-119">Creating a User Defined Table in Visual C#</span></span>  
 <span data-ttu-id="f0b70-120">이 예에서는 `StringCollection` 형식을 포함하는 클래스 라이브러리에 대해 imports 문을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-120">For this example, you will have to include an imports statement for the class library that contains the `StringCollection` type.</span></span>  
  
 `using System.Collections.Specialized;`  
  
 <span data-ttu-id="f0b70-121">이 예는 사용자 정의 테이블을 만들어 사용자 정의 함수의 매개 변수로 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-121">The example shows how to create a user-defined table, and then how to use it as a parameter in a user-defined function.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server   
               Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
            //Define a UserDefinedTableType object variable by supplying the  
            //database and name in the constructor.   
         UserDefinedTableType udtt = new UserDefinedTableType(db, "My_User_Defined_Table");  
  
            //Add three columns of different types to the   
            //UserDefinedTableType object.   
         udtt.Columns.Add(new Column(udtt, "Col1", DataType.Int));  
         udtt.Columns.Add(new Column(udtt, "Col2", DataType.VarCharMax));  
         udtt.Columns.Add(new Column(udtt, "Col3", DataType.Money));  
  
            //Define an Index object variable by supplying the user-defined   
            //table variable and name in the constructor.   
  
            Index idx = new Index(udtt, "PK_UddtTable");  
  
            //Add the first column in the user-defined table as   
            //the indexed column.   
            idx.IndexedColumns.Add(new IndexedColumn(idx, "Col1"));  
            //Specify that the index is a clustered, unique, primary key.   
            idx.IsClustered = true;  
            idx.IsUnique = true;  
            idx.IndexKeyType = IndexKeyType.DriPrimaryKey;  
            udtt.Indexes.Add(idx);  
            //Add the index and create the user-defined table.   
            udtt.Create();  
  
            //Display the Transact-SQL creation script for the   
            //user-defined table.   
            System.Collections.Specialized.StringCollection sc;  
            sc = udtt.Script();  
            foreach (string s in sc)  
            {  
                Console.WriteLine(s);  
            }  
  
            //Define a new user-defined function with a single parameter.  
            UserDefinedFunction udf = new UserDefinedFunction(db, "My_User_Defined_Function");  
            udf.TextMode = false;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
            udf.DataType = DataType.DateTime;  
  
            //Specify the parameter as a UserDefinedTableTable object.  
             UserDefinedFunctionParameter udfp = new UserDefinedFunctionParameter(udf, "@param");  
            udfp.DataType = new DataType(udtt);  
            udfp.IsReadOnly = true;  
            udf.Parameters.Add(udfp);  
  
            //Specify the TextBody property to the Transact-SQL definition of the   
            //user-defined function.   
            udf.TextBody = "BEGIN RETURN (GETDATE());end";  
            //Create the user-defined function.   
            udf.Create();  
        }  
```  
  
## <a name="creating-a-user-defined-table-in-powershell"></a><span data-ttu-id="f0b70-122">PowerShell에서 사용자 정의 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="f0b70-122">Creating a User Defined Table in PowerShell</span></span>  
 <span data-ttu-id="f0b70-123">이 예에서는 `StringCollection` 형식을 포함하는 클래스 라이브러리에 대해 imports 문을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-123">For this example, you will have to include an imports statement for the class library that contains the `StringCollection` type.</span></span>  
  
 `using System.Collections.Specialized;`  
  
 <span data-ttu-id="f0b70-124">이 예는 사용자 정의 테이블을 만들어 사용자 정의 함수의 매개 변수로 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0b70-124">The example shows how to create a user-defined table, and then how to use it as a parameter in a user-defined function.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
#Define a UserDefinedTableType object variable by supplying the  
#database and name in the constructor.
$udtt = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedTableType -ArgumentList $db, "My_User_Defined_Table"  
  
#Add three columns of different types to the UserDefinedTableType object.  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::Int  
$col = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -ArgumentList $udtt, "col1", $type  
$udtt.Columns.Add($col)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::VarCharMax  
$col = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -ArgumentList $udtt, "col2", $type  
$udtt.Columns.Add($col)  
  
 $type = [Microsoft.SqlServer.Management.SMO.DataType]::Money  
$col = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -ArgumentList $udtt, "col3", $type  
$udtt.Columns.Add($col)
  
#Define an Index object variable by supplying the user-defined table variable and name in the constructor.
$idx = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Index `  
-argumentlist $udtt, "PK_UddtTable"  
  
#Add the first column in the user-defined table as the indexed column.
$idxcol = New-Object -TypeName Microsoft.SqlServer.Management.SMO.IndexedColumn `  
-argumentlist $idx, "Col1"  
$idx.IndexedColumns.Add($idxcol)  
  
#Specify that the index is a clustered, unique, primary key.
$idx.IsClustered = $true  
$idx.IsUnique = $true  
$idx.IndexKeyType = [Microsoft.SqlServer.Management.SMO.IndexKeyType]::DriPrimaryKey;  
  
#Add the index and create the user-defined table.
$udtt.Indexes.Add($idx)  
$udtt.Create();  
  
# Display the Transact-SQL creation script for the user-defined table.
$sc = $udtt.Script()  
$sc  
  
# Define a new user-defined function with a single parameter.
$udf = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction -ArgumentList $db, "My_User_Defined_Function"  
$udf.TextMode = $false  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
  
# Specify the parameter as a UserDefinedTableTable object.  
$udfp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter -ArgumentList $udf, "@param"  
$type = New-Object -TypeName Microsoft.SqlServer.Management.SMO.DataType -ArgumentList $udtt  
$udfp.DataType = $type  
$udfp.IsReadOnly = $true  
$udf.Parameters.Add($udfp)  
  
# Specify the TextBody property to the Transact-SQL definition of the user-defined function.   
$udf.TextBody = "BEGIN RETURN (GETDATE());end"  
  
# Create the user-defined function.
$udf.Create()
```  
  
## <a name="see-also"></a><span data-ttu-id="f0b70-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0b70-125">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.FileGroup>   
 [<span data-ttu-id="f0b70-126">데이터베이스 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="f0b70-126">Database Files and Filegroups</span></span>](../../databases/database-files-and-filegroups.md)  
