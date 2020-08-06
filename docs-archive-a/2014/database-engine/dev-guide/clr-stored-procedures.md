---
title: CLR 저장 프로시저 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f8c69435e28bfa67c72e26b7a54e419cd91ef220
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648539"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="88da8-102">CLR 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="88da8-102">CLR Stored Procedures</span></span>
  <span data-ttu-id="88da8-103">저장 프로시저는 스칼라 식에서 사용할 수 없는 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="88da8-104">스칼라 함수와 달리 저장 프로시저는 테이블 형식의 결과와 메시지를 클라이언트에 반환하고 DDL(데이터 정의 언어) 및 DML(데이터 조작 언어) 문을 호출하고 출력 매개 변수를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-104">Unlike scalar functions, they can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span> <span data-ttu-id="88da8-105">CLR 통합의 장점 및 관리 코드와 관리 코드를 선택 하는 방법에 대 한 자세한 내용은 [!INCLUDE[tsql](../../includes/tsql-md.md)] [Clr 통합 개요](../../relational-databases/clr-integration/clr-integration-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88da8-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-stored-procedures"></a><span data-ttu-id="88da8-106">CLR 저장 프로시저에 대한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="88da8-106">Requirements for CLR Stored Procedures</span></span>  
 <span data-ttu-id="88da8-107">CLR (공용 언어 런타임)에서 저장 프로시저는 어셈블리의 클래스에 대 한 공용 정적 메서드로 구현 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="88da8-107">In the common language runtime (CLR), stored procedures are implemented as public static methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assembly.</span></span> <span data-ttu-id="88da8-108">정적 메서드는 void로 선언되거나 정수 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-108">The static method can either be declared as void, or return an integer value.</span></span> <span data-ttu-id="88da8-109">정적 메서드가 정수 값을 반환하는 경우 반환되는 정수는 프로시저의 반환 코드로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-109">If it returns an integer value, the integer returned is treated as the return code from the procedure.</span></span> <span data-ttu-id="88da8-110">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-110">For example:</span></span>  
  
 `EXECUTE @return_status = procedure_name`  
  
 <span data-ttu-id="88da8-111">@return_status변수에는 메서드에서 반환 된 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-111">The @return_status variable will contain the value returned by the method.</span></span> <span data-ttu-id="88da8-112">메서드가 void로 선언된 경우에는 반환 코드가 0입니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-112">If the method is declared void, the return code is 0.</span></span>  
  
 <span data-ttu-id="88da8-113">메서드가 매개 변수를 사용하는 경우 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 구현의 매개 변수 수가 저장 프로시저의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 선언에 사용된 매개 변수 수와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-113">If the method takes parameters, the number of parameters in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementation should be the same as the number of parameters used in the [!INCLUDE[tsql](../../includes/tsql-md.md)] declaration of the stored procedure.</span></span>  
  
 <span data-ttu-id="88da8-114">관리 코드에 해당 형식이 있는 모든 네이티브 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식의 매개 변수를 CLR 저장 프로시저에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-114">Parameters passed to a CLR stored procedure can be any of the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types that have an equivalent in managed code.</span></span> <span data-ttu-id="88da8-115">[!INCLUDE[tsql](../../includes/tsql-md.md)] 구문으로 프로시저를 만들려면 이러한 형식을 지정할 때 가장 가까운 네이티브 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-115">For the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax to create the procedure, these types should be specified with the most appropriate native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type equivalent.</span></span> <span data-ttu-id="88da8-116">형식 변환에 대 한 자세한 내용은 [CLR 매개 변수 데이터 매핑](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88da8-116">For more information about type conversions, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="88da8-117">테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="88da8-117">Table-Valued Parameters</span></span>  
 <span data-ttu-id="88da8-118">프로시저 또는 함수로 전달되는 사용자 정의 테이블 형식인 TVP(테이블 반환 매개 변수)를 사용하면 여러 개의 데이터 행을 서버로 편리하게 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-118">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="88da8-119">TVP는 매개 변수 배열과 유사한 기능을 제공하지만 더 유연하며 [!INCLUDE[tsql](../../includes/tsql-md.md)]과 더 밀접하게 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-119">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="88da8-120">또한 성능도 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-120">They also provide the potential for better performance.</span></span> <span data-ttu-id="88da8-121">TVP는 또한 서버와의 왕복 횟수를 줄이는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-121">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="88da8-122">스칼라 매개 변수 목록과 같이 서버로 여러 개의 요청을 보내는 대신 서버에 데이터를 TVP로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-122">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="88da8-123">사용자 정의 테이블 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스에서 실행 중인 관리되는 저장 프로시저 또는 함수에 테이블 반환 매개 변수로 전달되거나 이러한 저장 프로시저 또는 함수에서 테이블 반환 매개 변수로 반환될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-123">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="88da8-124">Tvp에 대 한 자세한 내용은 [데이터베이스 엔진&#41;&#40;테이블 반환 매개 변수 사용 ](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88da8-124">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="returning-results-from-clr-stored-procedures"></a><span data-ttu-id="88da8-125">CLR 저장 프로시저에서 결과 반환</span><span class="sxs-lookup"><span data-stu-id="88da8-125">Returning Results from CLR Stored Procedures</span></span>  
 <span data-ttu-id="88da8-126">출력 매개 변수, 테이블 형식 결과 및 메시지 등의 여러 가지 방법으로 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 저장 프로시저에서</span><span class="sxs-lookup"><span data-stu-id="88da8-126">Information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures in several ways.</span></span> <span data-ttu-id="88da8-127">정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-127">This includes output parameters, tabular results, and messages.</span></span>  
  
### <a name="output-parameters-and-clr-stored-procedures"></a><span data-ttu-id="88da8-128">OUTPUT 매개 변수 및 CLR 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="88da8-128">OUTPUT Parameters and CLR Stored Procedures</span></span>  
 <span data-ttu-id="88da8-129">[!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저와 마찬가지로 OUTPUT 매개 변수를 사용하여 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 저장 프로시저에서 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-129">As with [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures using OUTPUT parameters.</span></span> <span data-ttu-id="88da8-130">[!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저를 만드는 데 사용하는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] DML 구문은 [!INCLUDE[tsql](../../includes/tsql-md.md)]로 작성된 저장 프로시저를 만드는 데 사용하는 구문과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-130">The [!INCLUDE[tsql](../../includes/tsql-md.md)] DML syntax used for creating [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures is the same as that used for creating stored procedures written in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="88da8-131">구현 코드의 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스에 있는 해당 매개 변수는 참조 전달(pass-by-reference) 매개 변수를 인수로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-131">The corresponding parameter in the implementation code in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="88da8-132">Visual Basic는 c #에서와 동일한 방식으로 출력 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-132">Note that Visual Basic does not support output parameters in the same way that C# does.</span></span> <span data-ttu-id="88da8-133">다음과 같이 매개 변수를 참조로 지정 하 고 \<Out()> 특성을 적용 하 여 출력 매개 변수를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-133">You must specify the parameter by reference and apply the \<Out()> attribute to represent an OUTPUT parameter, as in the following:</span></span>  
  
```vb
Imports System.Runtime.InteropServices  
...  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 <span data-ttu-id="88da8-134">다음 코드는 OUTPUT 매개 변수를 통해 정보를 반환하는 저장 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-134">The following shows a stored procedure returning information through an OUTPUT parameter:</span></span>  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 <span data-ttu-id="88da8-135">위의 CLR 저장 프로시저가 포함 된 어셈블리를 서버에서 작성 하 고 만든 후에는 다음을 [!INCLUDE[tsql](../../includes/tsql-md.md)] 사용 하 여 데이터베이스에 프로시저를 만들고 *SUM* 을 OUTPUT 매개 변수로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-135">Once the assembly containing the above CLR stored procedure has been built and created on the server, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] is used to create the procedure in the database, and specifies *sum* as an OUTPUT parameter.</span></span>  
  
```sql
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 <span data-ttu-id="88da8-136">*Sum* 은 `int` SQL Server 데이터 형식으로 선언 되 고, clr 저장 프로시저에 정의 된 *값* 매개 변수는 clr 데이터 형식으로 지정 됩니다 `SqlInt32` .</span><span class="sxs-lookup"><span data-stu-id="88da8-136">Note that *sum* is declared as an `int` SQL Server data type, and that the *value* parameter defined in the CLR stored procedure is specified as a `SqlInt32` CLR data type.</span></span> <span data-ttu-id="88da8-137">호출 프로그램에서 CLR 저장 프로시저를 실행 하면에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `SqlInt32` clr 데이터 형식을 자동으로 `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-137">When a calling program executes the CLR stored procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically converts the `SqlInt32` CLR data type to an `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  <span data-ttu-id="88da8-138">변환할 수 있는 CLR 데이터 형식에 대 한 자세한 내용은 [Clr 매개 변수 데이터 매핑](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88da8-138">For more information about which CLR data types can and cannot be converted, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="88da8-139">테이블 형식 결과 및 메시지 반환</span><span class="sxs-lookup"><span data-stu-id="88da8-139">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="88da8-140">테이블 형식 결과 및 메시지를 클라이언트에 반환하려면 `SqlPipe` 개체를 사용합니다. 이 개체는 `Pipe` 클래스의 `SqlContext` 속성을 사용하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-140">Returning tabular results and messages to the client is done through the `SqlPipe` object, which is obtained by using the `Pipe` property of the `SqlContext` class.</span></span> <span data-ttu-id="88da8-141">`SqlPipe` 개체에는 `Send` 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-141">The `SqlPipe` object has a `Send` method.</span></span> <span data-ttu-id="88da8-142">`Send` 메서드를 호출하여 데이터를 파이프를 통해 호출 애플리케이션으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-142">By calling the `Send` method, you can transmit data through the pipe to the calling application.</span></span>  
  
 <span data-ttu-id="88da8-143">`SqlPipe.Send`를 보내는 메서드와 단순히 텍스트 문자열을 보내는 다른 메서드를 포함하여 `SqlDataReader` 메서드의 오버로드가 여러 개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-143">These are several overloads of the `SqlPipe.Send` method, including one that sends a `SqlDataReader` and another that simply sends a text string.</span></span>  
  
###### <a name="returning-messages"></a><span data-ttu-id="88da8-144">메시지 반환</span><span class="sxs-lookup"><span data-stu-id="88da8-144">Returning Messages</span></span>  
 <span data-ttu-id="88da8-145">`SqlPipe.Send(string)`를 사용하여 메시지를 클라이언트 애플리케이션에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-145">Use `SqlPipe.Send(string)` to send messages to the client application.</span></span> <span data-ttu-id="88da8-146">메시지 텍스트는 8000자로 제한되며</span><span class="sxs-lookup"><span data-stu-id="88da8-146">The text of the message is limited to 8000 characters.</span></span> <span data-ttu-id="88da8-147">8000자를 초과하면 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-147">If the message exceeds 8000 characters, it will be truncated.</span></span>  
  
###### <a name="returning-tabular-results"></a><span data-ttu-id="88da8-148">테이블 형식 결과 반환</span><span class="sxs-lookup"><span data-stu-id="88da8-148">Returning Tabular Results</span></span>  
 <span data-ttu-id="88da8-149">쿼리 결과를 직접 클라이언트로 보내려면 `Execute` 메서드 오버로드 중 하나를 `SqlPipe` 개체에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-149">To send the results of a query directly to the client, use one of the overloads of the `Execute` method on the `SqlPipe` object.</span></span> <span data-ttu-id="88da8-150">이 방법이 결과 집합을 가장 효율적으로 클라이언트에 반환하는 방법입니다. 그 이유는 데이터가 관리되는 메모리에 복사되지 않고 네트워크 버퍼로 전송되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-150">This is the most efficient way to return results to the client, since the data is transferred to the network buffers without being copied into managed memory.</span></span> <span data-ttu-id="88da8-151">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-151">For example:</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="88da8-152">앞서 실행한 쿼리 결과를 in-process 공급자를 통해 보내거나 사용자 지정 `SqlDataReader` 구현을 사용하여 데이터를 미리 처리하려면 `Send`를 사용하는 `SqlDataReader` 메서드의 오버로드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-152">To send the results of a query that was executed previously through the in-process provider (or to pre-process the data using a custom implementation of `SqlDataReader`), use the overload of the `Send` method that takes a `SqlDataReader`.</span></span> <span data-ttu-id="88da8-153">이 방법은 앞에서 설명한 직접적인 방법보다 조금 느리기는 하지만 데이터를 클라이언트로 보내기 전에 조작할 수 있다는 융통성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-153">This method is slightly slower than the direct method described previously, but it offers greater flexibility to manipulate the data before it is sent to the client.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
 
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="88da8-154">동적 결과 집합을 만들어 결과 집합을 채운 후 클라이언트로 보내려면 현재 연결에서 레코드를 만든 다음 `SqlPipe.Send`를 사용하여 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-154">To create a dynamic result set, populate it and send it to the client, you can create records from the current connection and send them using `SqlPipe.Send`.</span></span>  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 <span data-ttu-id="88da8-155">다음은 `SqlPipe`를 통해 테이블 형식 결과와 메시지를 보내는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-155">Here is an example of sending a tabular result and a message through `SqlPipe`.</span></span>  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 <span data-ttu-id="88da8-156">첫 번째 `Send`는 클라이언트에 메시지를 보내고 두 번째 Send는 `SqlDataReader`를 사용하여 테이블 형식 결과를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-156">The first `Send` sends a message to the client, while the second sends a tabular result using `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="88da8-157">이러한 예는 이해를 돕기 위한 목적으로만 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-157">Note that these examples are for illustrative purposes only.</span></span> <span data-ttu-id="88da8-158">계산을 많이 수행하는 애플리케이션의 경우 단순한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문보다 CLR 함수가 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-158">CLR functions are more appropriate than simple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for computation-intensive applications.</span></span> <span data-ttu-id="88da8-159">앞의 예와 거의 비슷한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-159">An almost equivalent [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure to the previous example is:</span></span>  
  
```sql
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  <span data-ttu-id="88da8-160">클라이언트 애플리케이션에서는 메시지와 결과 집합이 다른 방식으로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-160">Messages and result sets are retrieved differently in the client application.</span></span> <span data-ttu-id="88da8-161">예를 들어 결과 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 집합은 **결과** 뷰에 나타나고 메시지는 메시지 창에 표시 됩니다 **Messages** .</span><span class="sxs-lookup"><span data-stu-id="88da8-161">For instance, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] result sets appear in the **Results** view, and messages appear in the **Messages** pane.</span></span>  
  
 <span data-ttu-id="88da8-162">위의 Visual C# 코드를 MyFirstUdp.cs 파일에 저장한 경우 다음 코드를 사용하여 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-162">If the above Visual C# code is saved in a file MyFirstUdp.cs and compiled with:</span></span>  
  
```console
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 <span data-ttu-id="88da8-163">또는 위의 Visual Basic 코드를 MyFirstUdp.vb 파일에 저장한 경우 다음 코드를 사용하여 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-163">Or, if the above Visual Basic code is saved in a file MyFirstUdp.vb and compiled with:</span></span>  
  
```console
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  <span data-ttu-id="88da8-164">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 `/clr:pure`로 컴파일된 Visual C++ 데이터베이스 개체(예: 저장 프로시저)의 실행은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-164">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], Visual C++ database objects (such as stored procedures) compiled with `/clr:pure` are not supported for execution.</span></span>  
  
 <span data-ttu-id="88da8-165">결과 어셈블리를 등록한 후 다음 DDL을 사용하여 진입점을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88da8-165">The resulting assembly can be registered, and the entry point invoked, with the following DDL:</span></span>  
  
```sql
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a><span data-ttu-id="88da8-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88da8-166">See Also</span></span>  
 <span data-ttu-id="88da8-167">[CLR 사용자 정의 함수](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="88da8-167">[CLR User-Defined Functions](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="88da8-168">[CLR 사용자 정의 형식](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="88da8-168">[CLR User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 [<span data-ttu-id="88da8-169">CLR 트리거</span><span class="sxs-lookup"><span data-stu-id="88da8-169">CLR Triggers</span></span>](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  
