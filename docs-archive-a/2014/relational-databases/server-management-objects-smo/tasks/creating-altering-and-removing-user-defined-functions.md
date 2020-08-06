---
title: 사용자 정의 함수 생성, 변경 및 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9ff6d1b6e675d41e96f26fc24e6e0dd4ba69454
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660446"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a><span data-ttu-id="caa73-102">사용자 정의 함수 생성, 변경 및 제거</span><span class="sxs-lookup"><span data-stu-id="caa73-102">Creating, Altering, and Removing User-Defined Functions</span></span>
  <span data-ttu-id="caa73-103"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>개체는 사용자가에서 사용자 정의 함수를 프로그래밍 방식으로 관리할 수 있도록 하는 기능을 제공 합니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="caa73-103">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object provides functionality that lets users programmatically manage user-defined functions in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="caa73-104">사용자 정의 함수는 입력 및 출력 매개 변수를 지원하며 테이블 열에 대한 직접 참조도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-104">User-defined functions support input and output parameters, and also support direct references to table columns.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="caa73-105">의 저장 프로시저, 사용자 정의 함수, 트리거 및 사용자 정의 데이터 형식에서 어셈블리를 사용할 수 있으려면 먼저 데이터베이스에 어셈블리를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-105">requires assemblies to be registered within a database before these can be used inside stored procedures, user defined functions, triggers, and user defined data types.</span></span> <span data-ttu-id="caa73-106">SMO는 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 개체에서 이 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-106">SMO supports this feature with the <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object.</span></span>  
  
 <span data-ttu-id="caa73-107"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 개체는 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A> 및 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> 속성으로 .NET 어셈블리를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-107">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references the .NET assembly with the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> properties.</span></span>  
  
 <span data-ttu-id="caa73-108"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 개체가 .NET 어셈블리를 참조하는 경우 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 개체를 만들고 이를 <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> 개체에 속하는 <xref:Microsoft.SqlServer.Management.Smo.Database> 개체에 추가하여 어셈블리를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-108">When the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references a .NET assembly, you must register the assembly by creating a <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object and adding it to the <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> object, which belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa73-109">예제</span><span class="sxs-lookup"><span data-stu-id="caa73-109">Example</span></span>  
 <span data-ttu-id="caa73-110">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="caa73-111">자세한 내용은 visual [studio .net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 또는 [visual Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="caa73-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a><span data-ttu-id="caa73-112">Visual Basic에서 스칼라 사용자 정의 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="caa73-112">Creating a Scalar User-Defined Function in Visual Basic</span></span>  
 <span data-ttu-id="caa73-113">이 코드 예제는 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]에서 입력 <xref:System.DateTime> 개체 매개 변수와 정수 반환 형식을 사용하는 스칼라 사용자 정의 함수를 만들고 제거하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-113">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="caa73-114">사용자 정의 함수는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-114">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="caa73-115">이 예에서는 날짜 인수를 사용하여 ISO 주 번호를 계산하는 ISOweek라는 사용자 정의 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-115">The example creates a user-defined function, ISOweek, which takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="caa73-116">이 함수가 계산을 제대로 수행하기 위해서는 함수를 호출하기 전에 데이터베이스 DATEFIRST 옵션을 1로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-116">For this function to calculate correctly, the database DATEFIRST option must be set to 1 before the function is called.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a><span data-ttu-id="caa73-117">Visual C#에서 스칼라 사용자 정의 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="caa73-117">Creating a Scalar User-Defined Function in Visual C#</span></span>  
 <span data-ttu-id="caa73-118">이 코드 예제는 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]에서 입력 <xref:System.DateTime> 개체 매개 변수와 정수 반환 형식을 사용하는 스칼라 사용자 정의 함수를 만들고 제거하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-118">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="caa73-119">사용자 정의 함수는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-119">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="caa73-120">이 예에서는 사용자 정의 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-120">The example creates the user-defined function.</span></span> <span data-ttu-id="caa73-121">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="caa73-121">`ISOweek`.</span></span> <span data-ttu-id="caa73-122">이 함수는 날짜 인수를 사용하여 ISO 주 번호를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-122">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="caa73-123">이 함수가 계산을 제대로 수행하기 위해서는 함수를 호출하기 전에 데이터베이스 `DATEFIRST` 옵션을 `1` 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-123">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a><span data-ttu-id="caa73-124">PowerShell에서 스칼라 사용자 정의 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="caa73-124">Creating a Scalar User-Defined Function in PowerShell</span></span>  
 <span data-ttu-id="caa73-125">이 코드 예제는 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]에서 입력 <xref:System.DateTime> 개체 매개 변수와 정수 반환 형식을 사용하는 스칼라 사용자 정의 함수를 만들고 제거하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-125">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="caa73-126">사용자 정의 함수는 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 데이터베이스에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-126">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="caa73-127">이 예에서는 사용자 정의 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-127">The example creates the user-defined function.</span></span> <span data-ttu-id="caa73-128">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="caa73-128">`ISOweek`.</span></span> <span data-ttu-id="caa73-129">이 함수는 날짜 인수를 사용하여 ISO 주 번호를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-129">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="caa73-130">이 함수가 계산을 제대로 수행하기 위해서는 함수를 호출하기 전에 데이터베이스 `DATEFIRST` 옵션을 `1` 로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caa73-130">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction -argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter -argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.
$udf.Create()  
  
# Remove the user-defined function.
$udf.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="caa73-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="caa73-131">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
