---
title: 현재 트랜잭션 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
author: rothja
ms.author: jroth
ms.openlocfilehash: 34b7e67d30cb9d89a02eb918fcd03651b2915955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742303"
---
# <a name="accessing-the-current-transaction"></a><span data-ttu-id="30bb3-102">현재 트랜잭션 액세스</span><span class="sxs-lookup"><span data-stu-id="30bb3-102">Accessing the Current Transaction</span></span>
  <span data-ttu-id="30bb3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 실행되는 CLR(공용 언어 런타임) 코드를 입력하는 시점에 트랜잭션이 활성 상태인 경우 트랜잭션은 `System.Transactions.Transaction` 클래스를 통해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-103">If a transaction is active at the point at which common language runtime (CLR) code running on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is entered, the transaction is exposed through the `System.Transactions.Transaction` class.</span></span> <span data-ttu-id="30bb3-104">`Transaction.Current` 속성은 현재 트랜잭션에 액세스하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-104">The `Transaction.Current` property is used to access the current transaction.</span></span> <span data-ttu-id="30bb3-105">대부분의 경우 트랜잭션에 명시적으로 액세스할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-105">In most cases it is not necessary to access the transaction explicitly.</span></span> <span data-ttu-id="30bb3-106">데이터베이스 연결의 경우 ADO.NET에서는 `Transaction.Current` 메서드를 호출할 때 `Connection.Open`를 자동으로 검사하고 연결 문자열에서 `Enlist` 키워드가 false로 설정되지 않은 경우 연결을 트랜잭션에 투명하게 참여시킵니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-106">For database connections, ADO.NET checks `Transaction.Current` automatically when the `Connection.Open` method is called, and transparently enlists the connection in that transaction (unless the `Enlist` keyword is set to false in the connection string).</span></span>  
  
 <span data-ttu-id="30bb3-107">다음 시나리오에서는 `Transaction` 개체를 직접 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-107">You might want to use the `Transaction` object directly in the following scenarios:</span></span>  
  
-   <span data-ttu-id="30bb3-108">자동 참여를 수행하지 않거나 초기화 동안 몇 가지 이유로 참여하지 못한 리소스를 참여시키려는 경우</span><span class="sxs-lookup"><span data-stu-id="30bb3-108">If you want to enlist a resource that does not do automatic enlistment, or that for some reason was not enlisted during initialization.</span></span>  
  
-   <span data-ttu-id="30bb3-109">리소스를 트랜잭션에 명시적으로 참여시키려는 경우</span><span class="sxs-lookup"><span data-stu-id="30bb3-109">If you want to explicitly enlist a resource in the transaction.</span></span>  
  
-   <span data-ttu-id="30bb3-110">저장 프로시저 또는 함수 내에서 외부 트랜잭션을 종료하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="30bb3-110">If you want to terminate the external transaction from within your stored procedure or function.</span></span> <span data-ttu-id="30bb3-111">이 경우에는 <xref:System.Transactions.TransactionScope>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-111">In this case, you use <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="30bb3-112">예를 들어 다음 코드에서는 현재 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-112">For example, the following code will rollback the current transaction:</span></span>  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 <span data-ttu-id="30bb3-113">이 항목의 나머지 부분에서는 외부 트랜잭션을 취소하는 다른 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-113">The rest of this topic describes other ways to cancel an external transaction.</span></span>  
  
## <a name="canceling-an-external-transaction"></a><span data-ttu-id="30bb3-114">외부 트랜잭션 취소</span><span class="sxs-lookup"><span data-stu-id="30bb3-114">Canceling an External Transaction</span></span>  
 <span data-ttu-id="30bb3-115">관리되는 프로시저나 함수에서 다음과 같은 방법으로 외부 트랜잭션을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-115">You can cancel external transactions from a managed procedure or function in the following ways:</span></span>  
  
-   <span data-ttu-id="30bb3-116">관리되는 프로시저나 함수에서 출력 매개 변수를 사용하여 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-116">The managed procedure or function can return a value by using an output parameter.</span></span> <span data-ttu-id="30bb3-117">호출 [!INCLUDE[tsql](../../includes/tsql-md.md)] 프로시저는 반환된 값을 검사하고 해당되는 경우 `ROLLBACK TRANSACTION`을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-117">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can check the returned value and, if appropriate, execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="30bb3-118">관리되는 프로시저나 함수에서 사용자 지정 예외를 throw할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-118">The managed procedure or function can throw a custom exception.</span></span> <span data-ttu-id="30bb3-119">호출 하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 프로시저는 try/catch 블록에서 관리 되는 프로시저 또는 함수에 의해 throw 된 예외를 catch 하 고을 실행할 수 있습니다 `ROLLBACK TRANSACTION` .</span><span class="sxs-lookup"><span data-stu-id="30bb3-119">The calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure can catch the exception thrown by the managed procedure or function in a try/catch block and execute `ROLLBACK TRANSACTION`.</span></span>  
  
-   <span data-ttu-id="30bb3-120">관리되는 프로시저나 함수에서 특정 조건에 맞는 경우 `Transaction.Rollback` 메서드를 호출하여 현재 트랜잭션을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-120">The managed procedure or function can cancel the current transaction by calling the `Transaction.Rollback` method if a certain condition is met.</span></span>  
  
 <span data-ttu-id="30bb3-121">관리되는 프로시저나 함수 내에서 호출할 경우 `Transaction.Rollback` 메서드는 모호한 오류 메시지와 함께 예외를 throw하고 try/catch 블록에 래핑될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-121">When it is called within a managed procedure or function, the `Transaction.Rollback` method throws an exception with an ambiguous error message and can be wrapped in a try/catch block.</span></span> <span data-ttu-id="30bb3-122">오류 메시지는 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-122">The error message thresembles similar to the following:</span></span>  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 <span data-ttu-id="30bb3-123">이 예외는 예상된 것이며, 코드 실행을 계속하려면 try/catch 블록이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-123">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="30bb3-124">try/catch 블록이 없으면 즉시 예외가 호출 [!INCLUDE[tsql](../../includes/tsql-md.md)] 프로시저로 throw되고 관리되는 코드 실행이 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-124">Without the try/catch block, the exception will be immediately thrown to the calling [!INCLUDE[tsql](../../includes/tsql-md.md)] procedure and managed code execution will finish.</span></span> <span data-ttu-id="30bb3-125">관리되는 코드 실행이 완료되면 다른 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-125">When the managed code finishes execution, another exception is raised:</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 <span data-ttu-id="30bb3-126">이 예외도 예상된 것이며 실행을 계속하려면 트리거를 발생시키는 동작을 수행하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 try/catch 블록으로 둘러싸야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-126">This exception is also expected, and for execution to continue, you must have a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger.</span></span> <span data-ttu-id="30bb3-127">두 가지 예외가 throw되지만 트랜잭션이 롤백되고 변경 내용이 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-127">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed.</span></span>  
  
### <a name="example"></a><span data-ttu-id="30bb3-128">예제</span><span class="sxs-lookup"><span data-stu-id="30bb3-128">Example</span></span>  
 <span data-ttu-id="30bb3-129">다음은 `Transaction.Rollback` 메서드를 사용하여 관리되는 프로시저에서 트랜잭션을 롤백하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-129">The following is an example of a transaction being rolled back from a managed procedure by using the `Transaction.Rollback` method.</span></span> <span data-ttu-id="30bb3-130">관리되는 코드에서 `Transaction.Rollback` 메서드는 try/catch 블록으로 둘러싸여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-130">Notice the try/catch block around the `Transaction.Rollback` method in the managed code.</span></span> <span data-ttu-id="30bb3-131">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트는 어셈블리 및 관리되는 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-131">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates an assembly and managed stored procedure.</span></span> <span data-ttu-id="30bb3-132">`EXEC uspRollbackFromProc`문이 try/catch 블록에 래핑되어 관리 되는 프로시저의 실행이 완료 될 때 throw 되는 예외가 catch 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30bb3-132">Be aware that the `EXEC uspRollbackFromProc` statement is wrapped in a try/catch block, so that the exception thrown when the managed procedure completes execution is caught.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="30bb3-133">**Transact-SQL**</span><span class="sxs-lookup"><span data-stu-id="30bb3-133">**Transact-SQL**</span></span>  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="30bb3-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30bb3-134">See Also</span></span>  
 [<span data-ttu-id="30bb3-135">CLR 통합 및 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="30bb3-135">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
