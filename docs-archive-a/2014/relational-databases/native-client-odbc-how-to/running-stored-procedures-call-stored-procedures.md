---
title: 저장 프로시저 호출 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: rothja
ms.author: jroth
ms.openlocfilehash: d98d623dbbb4701bb59c95df502d0063d528d0d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650933"
---
# <a name="call-stored-procedures-odbc"></a><span data-ttu-id="9d925-102">저장 프로시저 호출(ODBC)</span><span class="sxs-lookup"><span data-stu-id="9d925-102">Call Stored Procedures (ODBC)</span></span>
  <span data-ttu-id="9d925-103">SQL 문이 ODBC CALL 이스케이프 절을 사용 하 여 저장 프로시저를 호출 하는 경우 Microsoft SQL Server 드라이버는 원격 RPC (저장 프로시저 호출) 메커니즘을 사용 하 여 SQL Server에 프로시저를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-103">When a SQL statement calls a stored procedure using the ODBC CALL escape clause, the Microsoft SQL Server driver sends the procedure to SQL Server using the remote stored procedure call (RPC) mechanism.</span></span> <span data-ttu-id="9d925-104">RPC 요청은 SQL Server의 문 구문 분석과 매개 변수 처리를 대부분 무시하므로 Transact-SQL EXECUTE 문을 사용할 때보다 속도가 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-104">RPC requests bypass much of the statement parsing and parameter processing in SQL Server and are faster than using the Transact-SQL EXECUTE statement.</span></span>  
  
 <span data-ttu-id="9d925-105">이 기능을 보여 주는 예제 응용 프로그램은 [ODBC&#41;&#40;반환 코드 및 출력 매개 변수 처리 ](running-stored-procedures-process-return-codes-and-output-parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d925-105">For a sample application that demonstrates this feature, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
### <a name="to-run-a-procedure-as-an-rpc"></a><span data-ttu-id="9d925-106">프로시저를 RPC로 실행하려면</span><span class="sxs-lookup"><span data-stu-id="9d925-106">To run a procedure as an RPC</span></span>  
  
1.  <span data-ttu-id="9d925-107">ODBC CALL 이스케이프 시퀀스를 사용하는 SQL 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-107">Construct a SQL statement that uses the ODBC CALL escape sequence.</span></span> <span data-ttu-id="9d925-108">이 문에서는 각 입/출력 및 출력 매개 변수와 프로시저 반환 값(있는 경우)에 대해 매개 변수 표식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-108">The statement uses parameter markers for each input, input/output, and output parameter, and for the procedure return value (if any):</span></span>  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  <span data-ttu-id="9d925-109">각 입력, 입/출력 및 출력 매개 변수와 프로시저 반환 값(있는 경우)에 대해 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-109">Call [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
3.  <span data-ttu-id="9d925-110">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)를 사용하여 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-110">Execute the statement with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d925-111">애플리케이션이 ODBC CALL 이스케이프 시퀀스가 아닌 Transact-SQL EXECUTE 구문을 사용하여 프로시저를 제출하는 경우 SQL Server ODBC 드라이버는 프로시저 호출을 RPC 대신 SQL 문으로 SQL Server에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-111">If an application submits a procedure using the Transact-SQL EXECUTE syntax (as opposed to the ODBC CALL escape sequence), the SQL Server ODBC driver passes the procedure call to SQL Server as a SQL statement rather than as an RPC.</span></span> <span data-ttu-id="9d925-112">또한 Transact-SQL EXECUTE 문을 사용하면 출력 매개 변수가 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d925-112">Also, output parameters are not returned if the Transact-SQL EXECUTE statement is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d925-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d925-113">See Also</span></span>  
 <span data-ttu-id="9d925-114">[저장 프로시저 실행 방법 항목 ODBC&#41;&#40;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="9d925-114">[Running Stored Procedures How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="9d925-115">[저장 프로시저 호출 일괄 처리](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md) </span><span class="sxs-lookup"><span data-stu-id="9d925-115">[Batching Stored Procedure Calls](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md) </span></span>  
 <span data-ttu-id="9d925-116">[저장 프로시저 실행](../native-client-odbc-stored-procedures/running-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9d925-116">[Running Stored Procedures](../native-client-odbc-stored-procedures/running-stored-procedures.md) </span></span>  
 <span data-ttu-id="9d925-117">[저장 프로시저 호출](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9d925-117">[Calling a Stored Procedure](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="9d925-118">절차</span><span class="sxs-lookup"><span data-stu-id="9d925-118">Procedures</span></span>](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
