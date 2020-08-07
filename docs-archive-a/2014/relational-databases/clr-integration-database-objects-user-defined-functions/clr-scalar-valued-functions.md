---
title: CLR 스칼라 반환 함수 | Microsoft Docs
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
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
ms.openlocfilehash: be8f9616fb285d6a68d6734924874ded06fb3bd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730751"
---
# <a name="clr-scalar-valued-functions"></a><span data-ttu-id="6418b-102">CLR 스칼라 반환 함수</span><span class="sxs-lookup"><span data-stu-id="6418b-102">CLR Scalar-Valued Functions</span></span>
  <span data-ttu-id="6418b-103">SVF(스칼라 반환 함수)는 문자열, 정수 또는 비트 값과 같은 단일 값을 반환합니다. .NET Framework 프로그래밍 언어를 사용하여 관리 코드에 스칼라 반환 사용자 정의 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-103">A scalar-valued function (SVF) returns a single value, such as a string, integer, or bit value.You can create scalar-valued user-defined functions in managed code using any .NET Framework programming language.</span></span> <span data-ttu-id="6418b-104">이러한 함수는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이나 다른 관리 코드에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-104">These functions are accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span> <span data-ttu-id="6418b-105">CLR 통합의 장점 및 관리 코드와 관리 코드를 선택 하는 방법에 대 한 자세한 내용은 [!INCLUDE[tsql](../../includes/tsql-md.md)] [Clr 통합 개요](../clr-integration/clr-integration-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6418b-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a><span data-ttu-id="6418b-106">CLR 스칼라 반환 함수에 대한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6418b-106">Requirements for CLR Scalar-Valued Functions</span></span>  
 <span data-ttu-id="6418b-107">.NET Framework SVF는 .NET Framework 어셈블리 클래스의 메서드로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-107">.NET Framework SVFs are implemented as methods on a class in a .NET Framework assembly.</span></span> <span data-ttu-id="6418b-108">SVF에서 반환 되는 입력 매개 변수 및 유형은,,,,,,, 또는를 제외 하 고에서 지원 되는 스칼라 데이터 형식 중 하나일 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `varchar` `char` `rowversion` `text` `ntext` `image` `timestamp` `table` `cursor` .</span><span class="sxs-lookup"><span data-stu-id="6418b-108">The input parameters and the type returned from a SVF can be any of the scalar data types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except `varchar`, `char`, `rowversion`, `text`, `ntext`, `image`, `timestamp`, `table`, or `cursor`.</span></span> <span data-ttu-id="6418b-109">SVF는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 구현 메서드의 반환 데이터 형식이 일치하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-109">SVFs must ensure a match between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and the return data type of the implementation method.</span></span> <span data-ttu-id="6418b-110">형식 변환에 대 한 자세한 내용은 [CLR 매개 변수 데이터 매핑](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6418b-110">For more information about type conversions, see [Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
 <span data-ttu-id="6418b-111">.NET Framework 언어로 .NET Framework SVF를 구현하는 경우 `SqlFunction` 사용자 지정 특성을 지정하여 함수에 대한 추가 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-111">When implementing a .NET Framework SVF in a .NET Framework language, the `SqlFunction` custom attribute can be specified to include additional information about the function.</span></span> <span data-ttu-id="6418b-112">`SqlFunction` 특성은 함수가 데이터를 액세스 또는 수정하는지, 결정적인지 여부 및 함수에 부동 소수점 연산이 포함되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-112">The `SqlFunction` attribute indicates whether or not the function accesses or modifies data, if it is deterministic, and if the function involves floating point operations.</span></span>  
  
 <span data-ttu-id="6418b-113">스칼라 반환 사용자 정의 함수는 결정적이거나 비결정적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-113">Scalar-valued user-defined functions may be deterministic or non-deterministic.</span></span> <span data-ttu-id="6418b-114">결정적 함수는 특정 입력 매개 변수 집합으로 호출될 때 항상 같은 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-114">A deterministic function always returns the same result when it is called with a specific set of input parameters.</span></span> <span data-ttu-id="6418b-115">비결정적 함수는 특정 입력 매개 변수 집합으로 호출될 때 다른 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-115">A non-deterministic function may return different results when it is called with a specific set of input parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6418b-116">함수가 동일한 입력 값과 동일한 데이터베이스 상태가 지정된 상태에서 항상 동일한 값을 출력하지 않을 경우에는 함수를 결정적인 함수로 표시하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="6418b-116">Do not mark a function as deterministic if the function does not always produces the same output values, given the same input values and the same database state.</span></span> <span data-ttu-id="6418b-117">실제로는 결정적인 함수가 아닌 함수를 결정적인 함수로 표시하면 인덱싱된 뷰 및 계산 열이 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-117">Marking a function as deterministic, when the function isn't truly deterministic can result in corrupted indexed views and computed columns.</span></span> <span data-ttu-id="6418b-118">`IsDeterministic` 속성을 true로 설정하여 함수를 결정적인 함수로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-118">You mark a function as deterministic by setting the `IsDeterministic` property to true.</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="6418b-119">테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="6418b-119">Table-Valued Parameters</span></span>  
 <span data-ttu-id="6418b-120">프로시저 또는 함수로 전달되는 사용자 정의 테이블 형식인 TVP(테이블 반환 매개 변수)를 사용하면 여러 개의 데이터 행을 서버로 편리하게 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-120">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="6418b-121">TVP는 매개 변수 배열과 유사한 기능을 제공하지만 더 유연하며 [!INCLUDE[tsql](../../includes/tsql-md.md)]과 더 밀접하게 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-121">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6418b-122">또한 성능도 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-122">They also provide the potential for better performance.</span></span> <span data-ttu-id="6418b-123">TVP는 또한 서버와의 왕복 횟수를 줄이는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-123">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="6418b-124">스칼라 매개 변수 목록과 같이 서버로 여러 개의 요청을 보내는 대신 서버에 데이터를 TVP로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-124">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="6418b-125">사용자 정의 테이블 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에서 실행 중인 관리되는 저장 프로시저 또는 함수에 테이블 반환 매개 변수로 전달되거나 이러한 저장 프로시저 또는 함수에서 테이블 반환 매개 변수로 반환될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-125">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="6418b-126">Tvp에 대 한 자세한 내용은 [데이터베이스 엔진&#41;&#40;테이블 반환 매개 변수 사용 ](../tables/use-table-valued-parameters-database-engine.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6418b-126">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="example-of-a-clr-scalar-valued-function"></a><span data-ttu-id="6418b-127">CLR 스칼라 반환 함수 예</span><span class="sxs-lookup"><span data-stu-id="6418b-127">Example of a CLR Scalar-Valued Function</span></span>  
 <span data-ttu-id="6418b-128">다음은 데이터를 액세스하고 정수 값을 반환하는 단순한 SVF입니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-128">Here is a simple SVF that accesses data and returns an integer value:</span></span>  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 <span data-ttu-id="6418b-129">코드의 첫 번째 줄에서는 `Microsoft.SqlServer.Server`를 참조하여 특성에 액세스하고 `System.Data.SqlClient`를 참조하여 ADO.NET 네임스페이스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-129">The first line of code references `Microsoft.SqlServer.Server` to access attributes and `System.Data.SqlClient` to access the ADO.NET namespace.</span></span> <span data-ttu-id="6418b-130">이 네임스페이스에는 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인 `SqlClient`가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-130">(This namespace contains `SqlClient`, the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="6418b-131">그런 다음 이 함수는 `SqlFunction` 네임스페이스에 있는 `Microsoft.SqlServer.Server` 사용자 지정 특성을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-131">Next, the function receives the `SqlFunction` custom attribute, which is found in the `Microsoft.SqlServer.Server` namespace.</span></span> <span data-ttu-id="6418b-132">사용자 지정 특성은 UDF(사용자 정의 함수)에서 in-process 공급자를 사용하여 서버의 데이터를 읽는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-132">The custom attribute indicates whether or not the user-defined function (UDF) uses the in-process provider to read data in the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6418b-133">에서 UDF로 데이터를 업데이트, 삽입 또는 삭제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-133">does not allow UDFs to update, insert, or delete data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6418b-134">는 in-process 공급자를 사용하지 않는 UDF의 실행을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-134">can optimize execution of a UDF that does not use the in-process provider.</span></span> <span data-ttu-id="6418b-135">이렇게 하려면 `DataAccessKind`를 `DataAccessKind.None`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-135">This is indicated by setting `DataAccessKind` to `DataAccessKind.None`.</span></span> <span data-ttu-id="6418b-136">다음 줄에서 대상 메서드는 public static(Visual Basic .NET의 경우 공유) 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-136">On the next line, the target method is a public static (shared in Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="6418b-137">`SqlContext` 네임스페이스에 있는 `Microsoft.SqlServer.Server` 클래스는 이미 설정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하여 `SqlCommand` 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-137">The `SqlContext` class, located in the `Microsoft.SqlServer.Server` namespace, can then access a `SqlCommand` object with a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is already set up.</span></span> <span data-ttu-id="6418b-138">여기서는 사용되지 않지만 `System.Transactions` API(응용 프로그래밍 인터페이스)를 통해 현재 트랜잭션 컨텍스트를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-138">Although not used here, the current transaction context is also available through the `System.Transactions` application programming interface (API).</span></span>  
  
 <span data-ttu-id="6418b-139">함수 본문에 있는 대부분의 줄은 `System.Data.SqlClient` 네임스페이스에 있는 형식을 사용하는 클라이언트 애플리케이션을 작성해 본 개발자에게 익숙한 코드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-139">Most of the lines of code in the function body should look familiar to developers who have written client applications that use the types found in the `System.Data.SqlClient` namespace.</span></span>  
  
 <span data-ttu-id="6418b-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="6418b-140">[C#]</span></span>  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 <span data-ttu-id="6418b-141">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="6418b-141">[Visual Basic]</span></span>  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 <span data-ttu-id="6418b-142">`SqlCommand` 개체를 초기화하여 적절한 명령 텍스트가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-142">The appropriate command text is specified by initializing the `SqlCommand` object.</span></span> <span data-ttu-id="6418b-143">앞의 예에서는 `SalesOrderHeader` 테이블의 행 수를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-143">The previous example counts the number of rows in table `SalesOrderHeader`.</span></span> <span data-ttu-id="6418b-144">그런 다음 `ExecuteScalar` 개체의 `cmd` 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-144">Next, the `ExecuteScalar` method of the `cmd` object is called.</span></span> <span data-ttu-id="6418b-145">이렇게 하면 쿼리를 기반으로 `int` 형식의 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-145">This returns a value of type `int` based on the query.</span></span> <span data-ttu-id="6418b-146">마지막으로 주문 횟수가 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-146">Finally, the order count is returned to the caller.</span></span>  
  
 <span data-ttu-id="6418b-147">이 코드를 FirstUdf.cs라는 파일에 저장하면 다음과 같이 어셈블리로 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-147">If this code is saved in a file called FirstUdf.cs, it could be compiled into as assembly as follows:</span></span>  
  
 <span data-ttu-id="6418b-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="6418b-148">[C#]</span></span>  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 <span data-ttu-id="6418b-149">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="6418b-149">[Visual Basic]</span></span>  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6418b-150">`/t:library`는 실행 파일 대신 라이브러리를 생성해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-150">`/t:library` indicates that a library, rather than an executable, should be produced.</span></span> <span data-ttu-id="6418b-151">실행 파일은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-151">Executables cannot be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6418b-152">`/clr:pure`로 컴파일된 Visual C++ 데이터베이스 개체는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-152">Visual C++ database objects compiled with `/clr:pure` are not supported for execution on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6418b-153">예를 들어 이러한 데이터베이스 개체에는 스칼라 반환 함수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-153">For example, such database objects include scalar-valued functions.</span></span>  
  
 <span data-ttu-id="6418b-154">어셈블리 및 UDF를 등록하는 예제 호출과 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-154">The [!INCLUDE[tsql](../../includes/tsql-md.md)] query and a sample invocation to register the assembly and UDF are:</span></span>  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 <span data-ttu-id="6418b-155">[!INCLUDE[tsql](../../includes/tsql-md.md)] 에 표시된 함수 이름이 대상 public static 메서드의 이름과 일치할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6418b-155">Note that the function name as exposed in [!INCLUDE[tsql](../../includes/tsql-md.md)] does not need to match the name of the target public static method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6418b-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6418b-156">See Also</span></span>  
 <span data-ttu-id="6418b-157">[CLR 매개 변수 데이터 매핑](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span><span class="sxs-lookup"><span data-stu-id="6418b-157">[Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span></span>  
 <span data-ttu-id="6418b-158">[CLR 통합 사용자 지정 특성 개요](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="6418b-158">[Overview of CLR Integration Custom Attributes](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span></span>  
 <span data-ttu-id="6418b-159">[사용자 정의 함수](../user-defined-functions/user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="6418b-159">[User-Defined Functions](../user-defined-functions/user-defined-functions.md) </span></span>  
 [<span data-ttu-id="6418b-160">CLR 데이터베이스 개체에서 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="6418b-160">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
