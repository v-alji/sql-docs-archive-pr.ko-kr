---
title: SqlPipe 개체 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 0044815a0b20d72b48b87bfe8f693d7196aaeaf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652162"
---
# <a name="sqlpipe-object"></a><span data-ttu-id="9b922-102">SqlPipe 개체</span><span class="sxs-lookup"><span data-stu-id="9b922-102">SqlPipe Object</span></span>
  <span data-ttu-id="9b922-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이전 버전에서는 결과나 출력 매개 변수를 호출 클라이언트로 보내는 저장 프로시저(또는 확장 저장 프로시저)를 작성하는 것이 일반적이었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-103">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is very common to write a stored procedure (or an extended stored procedure) that sends results or output parameters to the calling client.</span></span>  
  
 <span data-ttu-id="9b922-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저에서 0개 이상의 행을 반환하는 `SELECT` 문은 결과를 연결된 호출자의 "파이프"로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-104">In a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, any `SELECT` statement that returns zero or more rows sends the results to the connected caller's "pipe."</span></span>  
  
 <span data-ttu-id="9b922-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행되는 CLR(공용 언어 런타임) 데이터베이스 개체의 경우 `Send` 개체의 `SqlPipe` 메서드를 사용하여 결과를 연결된 파이프로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-105">For common language runtime (CLR) database objects running in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can send results to the connected pipe using the `Send` methods of the `SqlPipe` object.</span></span> <span data-ttu-id="9b922-106">`Pipe` 개체의 `SqlContext` 속성에 액세스하여 `SqlPipe` 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-106">Access the `Pipe` property of the `SqlContext` object to obtain the `SqlPipe` object.</span></span> <span data-ttu-id="9b922-107">`SqlPipe` 클래스는 개념상 ASP.NET에 있는 `Response` 클래스와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-107">The `SqlPipe` class is conceptually similar to the `Response` class found in ASP.NET.</span></span> <span data-ttu-id="9b922-108">자세한 내용은 .NET Framework 소프트웨어 개발 키트의 SqlPipe 클래스 참조 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b922-108">For more information, see the SqlPipe Class reference documentation in the .NET Framework software development kit.</span></span>  
  
## <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="9b922-109">테이블 형식 결과 및 메시지 반환</span><span class="sxs-lookup"><span data-stu-id="9b922-109">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="9b922-110">`SqlPipe`에는 3개의 오버로드가 있는 `Send` 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-110">The `SqlPipe` has a `Send` method, which has three overloads.</span></span> <span data-ttu-id="9b922-111">아래에 이 계정과 키의 예제가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-111">They are:</span></span>  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 <span data-ttu-id="9b922-112">`Send` 메서드는 클라이언트 또는 호출자에게 직접 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-112">The `Send` method sends data straight to the client or caller.</span></span> <span data-ttu-id="9b922-113">일반적으로 클라이언트에서 `SqlPipe`의 출력을 사용하지만, 중첩된 CLR 저장 프로시저의 경우 출력 소비자는 저장 프로시저일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-113">It is usually the client that consumes the output from the `SqlPipe`, but in the case of nested CLR stored procedures the output consumer can also be a stored procedure.</span></span> <span data-ttu-id="9b922-114">예를 들어 Procedure1은 명령 텍스트 "EXEC Procedure2"를 사용하여 SqlCommand.ExecuteReader()를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-114">For example, Procedure1 calls SqlCommand.ExecuteReader() with the command text "EXEC Procedure2".</span></span> <span data-ttu-id="9b922-115">Procedure2도 관리되는 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-115">Procedure2 is also a managed stored procedure.</span></span> <span data-ttu-id="9b922-116">이제 Procedure2에서 SqlPipe.Send( SqlDataRecord )를 호출하면 행은 호출자가 아닌 Procedure1의 판독기로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-116">If Procedure2 now calls SqlPipe.Send( SqlDataRecord ), the row is sent to Procedure1's reader, not the client.</span></span>  
  
 <span data-ttu-id="9b922-117">`Send` 메서드는 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 PRINT와 동등한 정보 메시지로 클라이언트에 표시되는 문자열 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-117">The `Send` method sends a string message that appears on the client as an information message, equivalent to PRINT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9b922-118">`SqlDataRecord`를 사용하여 단일 행 결과 집합을 보내거나 `SqlDataReader`를 사용하여 다중 행 결과 집합을 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-118">It can also send a single-row result-set using `SqlDataRecord`, or a multi-row result-set using a `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="9b922-119">또한 `SqlPipe` 개체에는 `ExecuteAndSend` 메서드도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-119">The `SqlPipe` object also has an `ExecuteAndSend` method.</span></span> <span data-ttu-id="9b922-120">이 메서드를 사용하여 `SqlCommand` 개체로 전달된 명령을 실행하고 결과를 직접 호출자에게 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-120">This method can be used to execute a command (passed as a `SqlCommand` object) and send results directly back to the caller.</span></span> <span data-ttu-id="9b922-121">전송된 명령에 오류가 있으면 예외를 파이프로 보내지만 호출 관리 코드에도 복사본을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-121">If there are errors in the command that was submitted, exceptions are sent to the pipe, but a copy is also sent to calling managed code.</span></span> <span data-ttu-id="9b922-122">호출 코드에서 예외를 catch하지 않을 경우 해당 예외는 스택을 통해 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드에 전파되고 출력에 두 번 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-122">If the calling code does not catch the exception, it propagates up the stack to the [!INCLUDE[tsql](../../includes/tsql-md.md)] code and appears in the output twice.</span></span> <span data-ttu-id="9b922-123">호출 코드에서 예외를 catch하지 않을 경우 파이프 소비자에게 오류가 표시되지만 중복 오류는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-123">If the calling code does catch the exception, the pipe consumer still sees the error, but there is not a duplicate error.</span></span>  
  
 <span data-ttu-id="9b922-124">이 메서드는 컨텍스트 연결과 관련된 `SqlCommand`만 사용할 수 있으며 비컨텍스트 연결과 관련된 명령은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-124">It can only take a `SqlCommand` that is associated with the context connection; it cannot take a command that is associated with the non-context connection.</span></span>  
  
## <a name="returning-custom-result-sets"></a><span data-ttu-id="9b922-125">사용자 지정 결과 집합 반환</span><span class="sxs-lookup"><span data-stu-id="9b922-125">Returning Custom Result Sets</span></span>  
 <span data-ttu-id="9b922-126">관리되는 저장 프로시저는 `SqlDataReader`에서 제공되지 않은 결과 집합을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-126">Managed stored procedures can send result sets that do not come from a `SqlDataReader`.</span></span> <span data-ttu-id="9b922-127">`SendResultsStart` 메서드와 함께 `SendResultsRow` 및 `SendResultsEnd`를 사용하면 저장 프로시저에서 사용자 지정 결과 집합을 클라이언트로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-127">The `SendResultsStart` method, along with `SendResultsRow` and `SendResultsEnd`, allows stored procedures to send custom result sets to the client.</span></span>  
  
 <span data-ttu-id="9b922-128">`SendResultsStart`는 `SqlDataRecord`를 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-128">`SendResultsStart` takes a `SqlDataRecord` as an input.</span></span> <span data-ttu-id="9b922-129">결과 집합의 시작 부분을 표시하고 레코드 메타데이터를 사용하여 결과 집합을 설명하는 메타데이터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-129">It marks the beginning of a result set and uses the record metadata to construct the metadata that describes the result set.</span></span> <span data-ttu-id="9b922-130">레코드 값은 `SendResultsStart`와 함께 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-130">It does not send the value of the record with `SendResultsStart`.</span></span> <span data-ttu-id="9b922-131">`SendResultsRow`를 사용하여 보낸 이후의 모든 행은 이 메타데이터 정의와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-131">All the subsequent rows, sent using `SendResultsRow`, must match that metadata definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b922-132">`SendResultsStart` 메서드를 호출한 후에는 `SendResultsRow` 및 `SendResultsEnd`만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-132">After calling the `SendResultsStart` method only `SendResultsRow` and `SendResultsEnd` can be called.</span></span> <span data-ttu-id="9b922-133">동일한 `SqlPipe` 인스턴스의 다른 메서드를 호출하면 `InvalidOperationException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-133">Calling any other method in the same instance of `SqlPipe` causes an `InvalidOperationException`.</span></span> <span data-ttu-id="9b922-134">`SendResultsEnd`는 `SqlPipe`를 다른 메서드가 호출될 수 있는 초기 상태로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-134">`SendResultsEnd` sets `SqlPipe` back to the initial state in which other methods can be called.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9b922-135">예제</span><span class="sxs-lookup"><span data-stu-id="9b922-135">Example</span></span>  
 <span data-ttu-id="9b922-136">`uspGetProductLine` 저장 프로시저는 지정한 제품 라인 내 모든 제품의 이름, 제품 번호, 색 및 목록 가격을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-136">The `uspGetProductLine` stored procedure returns the name, product number, color, and list price of all products within a specified product line.</span></span> <span data-ttu-id="9b922-137">이 저장 프로시저는 *prodLine*과 정확히 일치하는 항목만 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-137">This stored procedure accepts exact matches for *prodLine*.</span></span>  
  
 <span data-ttu-id="9b922-138">C#</span><span class="sxs-lookup"><span data-stu-id="9b922-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 <span data-ttu-id="9b922-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b922-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="9b922-140">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 투어링용 자전거 제품 목록을 반환하는 `uspGetProduct` 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9b922-140">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement executes the `uspGetProduct` procedure, which returns a list of touring bike products.</span></span>  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b922-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b922-141">See Also</span></span>  
 <span data-ttu-id="9b922-142">[SqlDataRecord 개체](sqldatarecord-object.md) </span><span class="sxs-lookup"><span data-stu-id="9b922-142">[SqlDataRecord Object](sqldatarecord-object.md) </span></span>  
 <span data-ttu-id="9b922-143">[CLR 저장 프로시저](../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9b922-143">[CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="9b922-144">ADO.NET에 대한 SQL Server In-Process 전용 확장</span><span class="sxs-lookup"><span data-stu-id="9b922-144">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
