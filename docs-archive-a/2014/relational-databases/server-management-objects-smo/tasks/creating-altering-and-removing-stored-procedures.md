---
title: 저장 프로시저 생성, 변경 및 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73e8313f3befd4c7c5cb20cdb6649c87ea72b037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660451"
---
# <a name="creating-altering-and-removing-stored-procedures"></a><span data-ttu-id="7a9b8-102">저장 프로시저 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="7a9b8-102">Creating, Altering, and Removing Stored Procedures</span></span>
  <span data-ttu-id="7a9b8-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects(SMO)에서 저장 프로시저는 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedures are represented by the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
 <span data-ttu-id="7a9b8-104">SMO에서 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 개체를 만들려면 저장 프로시저를 정의하는 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> 속성을 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-104">Creating a <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object in SMO requires setting the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> property to the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script that defines the stored procedure.</span></span> <span data-ttu-id="7a9b8-105">매개 변수에는 \@ 접두사가 필요 하며, 개체를 사용 하 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> 고 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> 개체의 컬렉션에를 추가 하 여 개별적으로 만들어야 합니다 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> .</span><span class="sxs-lookup"><span data-stu-id="7a9b8-105">Parameters require the \@ prefix and must be created individually by using <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> objects and adding to the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a9b8-106">예제</span><span class="sxs-lookup"><span data-stu-id="7a9b8-106">Example</span></span>  
 <span data-ttu-id="7a9b8-107">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="7a9b8-108">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a><span data-ttu-id="7a9b8-109">Visual Basic에서 저장 프로시저 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="7a9b8-109">Creating, Altering, and Removing a Stored Procedure in Visual Basic</span></span>  
 <span data-ttu-id="7a9b8-110">이 코드 예제는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 대한 저장 프로시저를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-110">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="7a9b8-111">이 예에서는 직원 ID 번호를 제공하면 직원의 성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-111">The example returns the last name of an employee when it is given the employee ID number.</span></span> <span data-ttu-id="7a9b8-112">저장 프로시저에는 직원 ID 번호를 지정하는 입력 매개 변수 하나와 직원의 성을 반환하는 출력 매개 변수 하나가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-112">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a><span data-ttu-id="7a9b8-113">Visual C#에서 저장 프로시저 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="7a9b8-113">Creating, Altering, and Removing a Stored Procedure in Visual C#</span></span>  
 <span data-ttu-id="7a9b8-114">이 코드 예제는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 대한 저장 프로시저를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-114">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="7a9b8-115">이 예에서는 직원 ID 번호(`BusinessEntityID`)를 제공하면 직원의 성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-115">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="7a9b8-116">저장 프로시저에는 직원 ID 번호를 지정하는 입력 매개 변수 하나와 직원의 성을 반환하는 출력 매개 변수 하나가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-116">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a><span data-ttu-id="7a9b8-117">PowerShell에서 저장 프로시저 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="7a9b8-117">Creating, Altering, and Removing a Stored Procedure in PowerShell</span></span>  
 <span data-ttu-id="7a9b8-118">이 코드 예제는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 대한 저장 프로시저를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-118">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="7a9b8-119">이 예에서는 직원 ID 번호(`BusinessEntityID`)를 제공하면 직원의 성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-119">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="7a9b8-120">저장 프로시저에는 직원 ID 번호를 지정하는 입력 매개 변수 하나와 직원의 성을 반환하는 출력 매개 변수 하나가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7a9b8-120">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.
$sp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure -argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.
$sp.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a9b8-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a9b8-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
