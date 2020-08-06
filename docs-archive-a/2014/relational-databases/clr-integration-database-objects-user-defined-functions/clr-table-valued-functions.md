---
title: CLR 테이블 반환 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- Transact-SQL table-valued functions
- table-valued functions [CLR integration]
- TVFs [CLR integration]
ms.assetid: 9a6133ea-36e9-45bf-b572-1c0df3d6c194
author: rothja
ms.author: jroth
ms.openlocfilehash: b700aba5a753ecd8ee50ee9b7679cafb2f1f8581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651730"
---
# <a name="clr-table-valued-functions"></a><span data-ttu-id="c6537-102">CLR 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="c6537-102">CLR Table-Valued Functions</span></span>
  <span data-ttu-id="c6537-103">테이블 반환 함수는 테이블을 반환하는 사용자 정의 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-103">A table-valued function is a user-defined function that returns a table.</span></span>  
  
 <span data-ttu-id="c6537-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 모든 관리 언어에서 테이블 반환 함수를 정의할 수 있도록 하여 테이블 반환 함수의 기능을 확장하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extends the functionality of table-valued functions by allowing you to define a table-valued function in any managed language.</span></span> <span data-ttu-id="c6537-105">데이터는 `IEnumerable` 또는 `IEnumerator` 개체를 통해 테이블 반환 함수에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-105">Data is returned from a table-valued function through an `IEnumerable` or `IEnumerator` object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6537-106">테이블 반환 함수의 경우 반환 테이블 형식의 열은 타임스탬프 열 또는 비유니코드 문자열 데이터 형식 열(예: `char`, `varchar` 및 `text`)을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-106">For table-valued functions, the columns of the return table type cannot include timestamp columns or non-Unicode string data type columns (such as `char`, `varchar`, and `text`).</span></span> <span data-ttu-id="c6537-107">NOT NULL 제약 조건은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-107">The NOT NULL constraint is not supported.</span></span>  
  
## <a name="differences-between-transact-sql-and-clr-table-valued-functions"></a><span data-ttu-id="c6537-108">Transact-SQL과 CLR 테이블 반환 함수의 차이</span><span class="sxs-lookup"><span data-stu-id="c6537-108">Differences Between Transact-SQL and CLR Table-Valued Functions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="c6537-109">테이블 반환 함수는 함수 호출의 결과를 중간 테이블로 구체화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-109">table-valued functions materialize the results of calling the function into an intermediate table.</span></span> <span data-ttu-id="c6537-110">TVF는 중간 테이블을 사용하므로 결과에 대해 제약 조건 및 고유 인덱스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-110">Since they use an intermediate table, they can support constraints and unique indexes over the results.</span></span> <span data-ttu-id="c6537-111">이러한 기능은 대규모의 결과가 반환할 때 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-111">These features can be extremely useful when large results are returned.</span></span>  
  
 <span data-ttu-id="c6537-112">반면 CLR 테이블 반환 함수는 스트리밍 방식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-112">In contrast, CLR table-valued functions represent a streaming alternative.</span></span> <span data-ttu-id="c6537-113">전체 결과 집합을 단일 테이블로 구체화할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-113">There is no requirement that the entire set of results be materialized in a single table.</span></span> <span data-ttu-id="c6537-114">관리 함수에서 반환된 `IEnumerable` 개체는 테이블 반환 함수를 호출하는 쿼리의 실행 계획에 의해 직접 호출되며 결과는 증분 방식으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-114">The `IEnumerable` object returned by the managed function is directly called by the execution plan of the query that calls the table-valued function, and the results are consumed in an incremental manner.</span></span> <span data-ttu-id="c6537-115">이 스트리밍 모델은 전체 테이블이 채워질 때까지 기다리지 않고 첫 번째 행을 사용할 수 있게 된 직후부터 결과를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-115">This streaming model ensures that results can be consumed immediately after the first row is available, instead of waiting for the entire table to be populated.</span></span> <span data-ttu-id="c6537-116">반환되는 행의 수가 매우 많은 경우에도 이러한 행을 메모리에서 전체적으로 구체화할 필요가 없는 이 방법이 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-116">It is also a better alternative if you have very large numbers of rows returned, because they do not have to be materialized in memory as a whole.</span></span> <span data-ttu-id="c6537-117">예를 들어 관리 테이블 반환 함수는 텍스트 파일을 구문 분석하고 각 줄을 하나의 행으로 반환하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-117">For example, a managed table-valued function could be used to parse a text file and return each line as a row.</span></span>  
  
## <a name="implementing-table-valued-functions"></a><span data-ttu-id="c6537-118">테이블 반환 함수 구현</span><span class="sxs-lookup"><span data-stu-id="c6537-118">Implementing Table-Valued Functions</span></span>  
 <span data-ttu-id="c6537-119">테이블 반환 함수를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 어셈블리 클래스의 메서드로 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-119">Implement table-valued functions as methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="c6537-120">테이블 반환 함수 코드는 `IEnumerable` 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-120">Your table-valued function code must implement the `IEnumerable` interface.</span></span> <span data-ttu-id="c6537-121">`IEnumerable` 인터페이스는 .NET Framework에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-121">The `IEnumerable` interface is defined in the .NET Framework.</span></span> <span data-ttu-id="c6537-122">.NET Framework의 배열 및 컬렉션을 나타내는 형식은 이미 `IEnumerable` 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-122">Types representing arrays and collections in the .NET Framework already implement the `IEnumerable` interface.</span></span> <span data-ttu-id="c6537-123">따라서 컬렉션 또는 배열을 결과 집합으로 변환하는 테이블 반환 함수를 손쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-123">This makes it easy for writing table-valued functions that convert a collection or an array into a result set.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="c6537-124">테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6537-124">Table-Valued Parameters</span></span>  
 <span data-ttu-id="c6537-125">테이블 반환 매개 변수는 프로시저 또는 함수로 전달되는 사용자 정의 테이블 형식이며 여러 개의 데이터 행을 서버로 편리하게 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-125">Table-valued parameters are user-defined table types that are passed into a procedure or function and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="c6537-126">테이블 반환 매개 변수는 매개 변수 배열과 유사한 기능을 제공하지만 더 유연하며 [!INCLUDE[tsql](../../includes/tsql-md.md)]과 더 밀접하게 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-126">Table-valued parameters provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c6537-127">또한 성능도 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-127">They also provide the potential for better performance.</span></span> <span data-ttu-id="c6537-128">또한 테이블 반환 매개 변수는 서버와의 왕복 횟수를 줄이는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-128">Table-valued parameters also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="c6537-129">스칼라 매개 변수 목록과 같이 서버로 여러 개의 요청을 보내는 대신 서버에 데이터를 테이블 반환 매개 변수로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-129">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a table-valued parameter.</span></span> <span data-ttu-id="c6537-130">사용자 정의 테이블 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에서 실행 중인 관리되는 저장 프로시저 또는 함수에 테이블 반환 매개 변수로 전달되거나 이러한 저장 프로시저 또는 함수에서 테이블 반환 매개 변수로 반환될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-130">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="c6537-131">테이블 반환 매개 변수에 관한 자세한 내용은 [Use Table-Valued Parameters&#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c6537-131">For more information about table-valued parameters, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="output-parameters-and-table-valued-functions"></a><span data-ttu-id="c6537-132">출력 매개 변수와 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="c6537-132">Output Parameters and Table-Valued Functions</span></span>  
 <span data-ttu-id="c6537-133">테이블 반환 함수에서 출력 매개 변수를 사용하여 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-133">Information may be returned from table-valued functions using output parameters.</span></span> <span data-ttu-id="c6537-134">구현 코드의 테이블 반환 함수에 있는 해당 매개 변수는 참조 전달(pass-by-reference) 매개 변수를 인수로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-134">The corresponding parameter in the implementation code table-valued function should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="c6537-135">Visual Basic은 Visual C#과 같은 방식으로 출력 매개 변수를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-135">Note that Visual Basic does not support output parameters in the same way that Visual C# does.</span></span> <span data-ttu-id="c6537-136">다음과 같이 매개 변수를 참조로 지정 하 고 \<Out()> 특성을 적용 하 여 출력 매개 변수를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-136">You must specify the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
...  
Public Shared Sub FillRow ( <Out()> ByRef value As SqlInt32)  
```  
  
### <a name="defining-a-table-valued-function-in-transact-sql"></a><span data-ttu-id="c6537-137">Transact-SQL에서 테이블 반환 함수 정의</span><span class="sxs-lookup"><span data-stu-id="c6537-137">Defining a Table-Valued Function in Transact-SQL</span></span>  
 <span data-ttu-id="c6537-138">CLR 테이블 반환 함수를 정의하는 구문은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 테이블 반환 함수를 정의하는 구문과 비슷하지만 `EXTERNAL NAME` 절이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-138">The syntax for defining a CLR table-valued function is similar to that of a [!INCLUDE[tsql](../../includes/tsql-md.md)] table-valued function, with the addition of the `EXTERNAL NAME` clause.</span></span> <span data-ttu-id="c6537-139">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-139">For example:</span></span>  
  
```  
CREATE FUNCTION GetEmpFirstLastNames()  
RETURNS TABLE (FirstName NVARCHAR(4000), LastName NVARCHAR(4000))  
EXTERNAL NAME MyDotNETAssembly.[MyNamespace.MyClassname]. GetEmpFirstLastNames;  
```  
  
 <span data-ttu-id="c6537-140">테이블 반환 함수는 다음과 같은 쿼리에서 추가 처리를 위해 관계형 형식으로 데이터를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-140">Table-valued functions are used to represent data in relational form for further processing in queries such as:</span></span>  
  
```  
select * from function();  
select * from tbl join function() f on tbl.col = f.col;  
select * from table t cross apply function(t.column);  
```  
  
 <span data-ttu-id="c6537-141">테이블 반환 함수는 다음 경우 테이블을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-141">Table-valued functions can return a table when:</span></span>  
  
-   <span data-ttu-id="c6537-142">스칼라 입력 인수에서 만들어지는 경우.</span><span class="sxs-lookup"><span data-stu-id="c6537-142">Created from scalar input arguments.</span></span> <span data-ttu-id="c6537-143">예: 쉼표로 구분된 숫자 문자열을 받아 이를 테이블로 피벗하는 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="c6537-143">For example, a table-valued function that takes a comma-delimited string of numbers and pivots them into a table.</span></span>  
  
-   <span data-ttu-id="c6537-144">외부 데이터에서 생성되는 경우.</span><span class="sxs-lookup"><span data-stu-id="c6537-144">Generated from external data.</span></span> <span data-ttu-id="c6537-145">예: 이벤트 로그를 읽고 이를 테이블로 노출하는 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="c6537-145">For example, a table-valued function that reads the event log and exposes it as a table.</span></span>  
  
 <span data-ttu-id="c6537-146">**참고** 테이블 반환 함수는 메서드의 쿼리를 통해서만 데이터 액세스를 수행할 수 있으며 [!INCLUDE[tsql](../../includes/tsql-md.md)] `InitMethod` 메서드에서는 수행할 수 없습니다 `FillRow` .</span><span class="sxs-lookup"><span data-stu-id="c6537-146">**Note** A table-valued function can only perform data access through a [!INCLUDE[tsql](../../includes/tsql-md.md)] query in the `InitMethod` method, and not in the `FillRow` method.</span></span> <span data-ttu-id="c6537-147">[!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리가 수행되는 경우 `InitMethod`는 `SqlFunction.DataAccess.Read` 특성 속성으로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-147">The `InitMethod` should be marked with the `SqlFunction.DataAccess.Read` attribute property if a [!INCLUDE[tsql](../../includes/tsql-md.md)] query is performed.</span></span>  
  
## <a name="a-sample-table-valued-function"></a><span data-ttu-id="c6537-148">예제 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="c6537-148">A Sample Table-Valued Function</span></span>  
 <span data-ttu-id="c6537-149">다음 테이블 반환 함수는 시스템 이벤트 로그의 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-149">The following table-valued function returns information from the system event log.</span></span> <span data-ttu-id="c6537-150">함수는 읽을 이벤트 로그의 이름을 포함하는 단일 문자열 인수를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-150">The function takes a single string argument containing the name of the event log to read.</span></span>  
  
###### <a name="sample-code"></a><span data-ttu-id="c6537-151">샘플 코드</span><span class="sxs-lookup"><span data-stu-id="c6537-151">Sample Code</span></span>  
  
```csharp  
using System;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Collections;  
using System.Data.SqlTypes;  
using System.Diagnostics;  
  
public class TabularEventLog  
{  
    [SqlFunction(FillRowMethodName = "FillRow")]  
    public static IEnumerable InitMethod(String logname)  
    {  
        return new EventLog(logname).Entries;    }  
  
    public static void FillRow(Object obj, out SqlDateTime timeWritten, out SqlChars message, out SqlChars category, out long instanceId)  
    {  
        EventLogEntry eventLogEntry = (EventLogEntry)obj;  
        timeWritten = new SqlDateTime(eventLogEntry.TimeWritten);  
        message = new SqlChars(eventLogEntry.Message);  
        category = new SqlChars(eventLogEntry.Category);  
        instanceId = eventLogEntry.InstanceId;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.Sql  
Imports Microsoft.SqlServer.Server  
Imports System.Collections  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Public Class TabularEventLog  
    <SqlFunction(FillRowMethodName:="FillRow")> _  
    Public Shared Function InitMethod(ByVal logname As String) As IEnumerable  
        Return New EventLog(logname).Entries  
    End Function  
  
    Public Shared Sub FillRow(ByVal obj As Object, <Out()> ByRef timeWritten As SqlDateTime, <Out()> ByRef message As SqlChars, <Out()> ByRef category As SqlChars, <Out()> ByRef instanceId As Long)  
        Dim eventLogEnTry As EventLogEntry = CType(obj, EventLogEntry)  
        timeWritten = New SqlDateTime(eventLogEnTry.TimeWritten)  
        message = New SqlChars(eventLogEnTry.Message)  
        category = New SqlChars(eventLogEnTry.Category)  
        instanceId = eventLogEnTry.InstanceId  
    End Sub  
End Class  
```  
  
###### <a name="declaring-and-using-the-sample-table-valued-function"></a><span data-ttu-id="c6537-152">예제 테이블 반환 함수 선언 및 사용</span><span class="sxs-lookup"><span data-stu-id="c6537-152">Declaring and Using the Sample Table-Valued Function</span></span>  
 <span data-ttu-id="c6537-153">예제 테이블 반환 함수가 컴파일되면 다음과 같이 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-153">After the sample table-valued function has been compiled, it can be declared in [!INCLUDE[tsql](../../includes/tsql-md.md)] like this:</span></span>  
  
```  
use master;  
-- Replace SQL_Server_logon with your SQL Server user credentials.  
GRANT EXTERNAL ACCESS ASSEMBLY TO [SQL_Server_logon];   
-- Modify the following line to specify a different database.  
ALTER DATABASE master SET TRUSTWORTHY ON;  
  
-- Modify the next line to use the appropriate database.  
CREATE ASSEMBLY tvfEventLog   
FROM 'D:\assemblies\tvfEventLog\tvfeventlog.dll'   
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
CREATE FUNCTION ReadEventLog(@logname nvarchar(100))  
RETURNS TABLE   
(logTime datetime,Message nvarchar(4000),Category nvarchar(4000),InstanceId bigint)  
AS   
EXTERNAL NAME tvfEventLog.TabularEventLog.InitMethod;  
GO  
```  
  
 <span data-ttu-id="c6537-154">/clr:pure로 컴파일된 Visual C++ 데이터베이스 개체는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-154">Visual C++ database objects compiled with /clr:pure are not supported for execution on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="c6537-155">예를 들어 이러한 데이터베이스 개체에는 테이블 반환 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-155">For example, such database objects include table-valued functions.</span></span>  
  
 <span data-ttu-id="c6537-156">예제를 테스트하려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="c6537-156">To test the sample, try the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
```  
-- Select the top 100 events,  
SELECT TOP 100 *  
FROM dbo.ReadEventLog(N'Security') as T;  
go  
  
-- Select the last 10 login events.  
SELECT TOP 10 T.logTime, T.Message, T.InstanceId   
FROM dbo.ReadEventLog(N'Security') as T  
WHERE T.Category = N'Logon/Logoff';  
go  
```  
  
## <a name="sample-returning-the-results-of-a-sql-server-query"></a><span data-ttu-id="c6537-157">예제: SQL Server 쿼리 결과 반환</span><span class="sxs-lookup"><span data-stu-id="c6537-157">Sample: Returning the Results of a SQL Server Query</span></span>  
 <span data-ttu-id="c6537-158">다음 예제에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 쿼리하는 테이블 반환 함수를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-158">The following sample shows a table-valued function that queries a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="c6537-159">이 예제에서는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 AdventureWorks Light 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-159">This sample uses the AdventureWorks Light database from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="c6537-160">[https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843)AdventureWorks를 다운로드 하는 방법에 대 한 자세한 내용은을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6537-160">See [https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843) for more information on downloading AdventureWorks.</span></span>  
  
 <span data-ttu-id="c6537-161">원본 코드 파일 FindInvalidEmails.cs 또는 FindInvalidEmails.vb를 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="c6537-161">Name your source code file FindInvalidEmails.cs or FindInvalidEmails.vb.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
  
using Microsoft.SqlServer.Server;  
  
public partial class UserDefinedFunctions {  
   private class EmailResult {  
      public SqlInt32 CustomerId;  
      public SqlString EmailAdress;  
  
      public EmailResult(SqlInt32 customerId, SqlString emailAdress) {  
         CustomerId = customerId;  
         EmailAdress = emailAdress;  
      }  
   }  
  
   public static bool ValidateEmail(SqlString emailAddress) {  
      if (emailAddress.IsNull)  
         return false;  
  
      if (!emailAddress.Value.EndsWith("@adventure-works.com"))  
         return false;  
  
      // Validate the address. Put any more rules here.  
      return true;  
   }  
  
   [SqlFunction(  
       DataAccess = DataAccessKind.Read,  
       FillRowMethodName = "FindInvalidEmails_FillRow",  
       TableDefinition="CustomerId int, EmailAddress nvarchar(4000)")]  
   public static IEnumerable FindInvalidEmails(SqlDateTime modifiedSince) {  
      ArrayList resultCollection = new ArrayList();  
  
      using (SqlConnection connection = new SqlConnection("context connection=true")) {  
         connection.Open();  
  
         using (SqlCommand selectEmails = new SqlCommand(  
             "SELECT " +  
             "[CustomerID], [EmailAddress] " +  
             "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " +  
             "WHERE [ModifiedDate] >= @modifiedSince",  
             connection)) {  
            SqlParameter modifiedSinceParam = selectEmails.Parameters.Add(  
                "@modifiedSince",  
                SqlDbType.DateTime);  
            modifiedSinceParam.Value = modifiedSince;  
  
            using (SqlDataReader emailsReader = selectEmails.ExecuteReader()) {  
               while (emailsReader.Read()) {  
                  SqlString emailAddress = emailsReader.GetSqlString(1);  
                  if (ValidateEmail(emailAddress)) {  
                     resultCollection.Add(new EmailResult(  
                         emailsReader.GetSqlInt32(0),  
                         emailAddress));  
                  }  
               }  
            }  
         }  
      }  
  
      return resultCollection;  
   }  
  
   public static void FindInvalidEmails_FillRow(  
       object emailResultObj,  
       out SqlInt32 customerId,  
       out SqlString emailAdress) {  
      EmailResult emailResult = (EmailResult)emailResultObj;  
  
      customerId = emailResult.CustomerId;  
      emailAdress = emailResult.EmailAdress;  
   }  
};  
```  
  
```vb  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, ByRef customerId As SqlInt32, ByRef emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End ClassImports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, customerId As SqlInt32, emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="c6537-162">원본 코드를 DLL로 컴파일한 다음 C 드라이브의 루트 디렉터리에 이 DLL을 복사한 후</span><span class="sxs-lookup"><span data-stu-id="c6537-162">Compile the source code to a DLL and copy the DLL to the root directory of your C drive.</span></span>  <span data-ttu-id="c6537-163">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c6537-163">Then, execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query.</span></span>  
  
```  
use AdventureWorksLT2008;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'FindInvalidEmails')  
   DROP FUNCTION FindInvalidEmails;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\FindInvalidEmails.dll'  
WITH PERMISSION_SET = SAFE -- EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION FindInvalidEmails(@ModifiedSince datetime)   
RETURNS TABLE (  
   CustomerId int,  
   EmailAddress nvarchar(4000)  
)  
AS EXTERNAL NAME MyClrCode.UserDefinedFunctions.[FindInvalidEmails];  
go  
  
SELECT * FROM FindInvalidEmails('2000-01-01');  
go  
```  
  
