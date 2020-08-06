---
title: 문 실행 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
ms.openlocfilehash: 3066a09cb1f5e63105ca3ffe2441f19e4bbe0101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646406"
---
# <a name="executing-statements-odbc"></a><span data-ttu-id="e2546-102">문 실행(ODBC)</span><span class="sxs-lookup"><span data-stu-id="e2546-102">Executing Statements (ODBC)</span></span>
  <span data-ttu-id="e2546-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 데이터베이스에서 SQL 문을 실행 하는 다양 한 방법을 제공 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2546-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers a variety ways to execute SQL statements in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="e2546-104">직접 실행</span><span class="sxs-lookup"><span data-stu-id="e2546-104">Direct execution</span></span>  
  
-   <span data-ttu-id="e2546-105">준비된 실행</span><span class="sxs-lookup"><span data-stu-id="e2546-105">Prepared execution</span></span>  
  
 <span data-ttu-id="e2546-106">직접 실행에는 문을 포함 하는 문자열을 작성 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 하 고 **Sqlexecdirect** 함수를 사용 하 여 실행을 위해 제출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2546-106">Direct execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submitting it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="e2546-107">준비된 실행에서는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문이 포함된 문자열을 작성한 다음 두 가지 단계로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e2546-107">Prepared execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and then executing it in two stages.</span></span> <span data-ttu-id="e2546-108">첫 번째 단계에서는 [Sqlprepare 함수](https://go.microsoft.com/fwlink/?LinkId=59360) 함수를 사용 하 여의 문에 대 한 실행 계획을 구문 분석 하 고 컴파일합니다 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2546-108">The first stage uses the [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) function to parse and compile the execution plan for the statement in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="e2546-109">두 번째 단계는 **Sqlexecute** 함수를 사용 하 여 이전에 준비 된 실행 계획을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2546-109">The second stage uses the **SQLExecute** function to execute the previously prepared execution plan.</span></span> <span data-ttu-id="e2546-110">이렇게 하면 각각의 실행에서 구문 분석 및 컴파일 오버헤드를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2546-110">This saves the parsing and compiling overhead on each execution.</span></span> <span data-ttu-id="e2546-111">준비된 실행은 애플리케이션에서 매개 변수가 있는 동일한 SQL 문을 반복적으로 실행하는 데 많이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2546-111">Prepared execution is commonly used by applications to repeatedly execute the same, parameterized SQL statement.</span></span>  
  
 <span data-ttu-id="e2546-112">직접 실행과 준비된 실행에서 모두 단일 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문이나 SQL 문의 일괄 처리를 실행하거나 저장 프로시저를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2546-112">Both direct and prepared execution can execute a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement or a batch of SQL statements, or they can call a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2546-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e2546-113">In This Section</span></span>  
  
-   [<span data-ttu-id="e2546-114">직접 실행</span><span class="sxs-lookup"><span data-stu-id="e2546-114">Direct Execution</span></span>](direct-execution.md)  
  
-   [<span data-ttu-id="e2546-115">준비된 실행</span><span class="sxs-lookup"><span data-stu-id="e2546-115">Prepared Execution</span></span>](prepared-execution.md)  
  
-   [<span data-ttu-id="e2546-116">절차</span><span class="sxs-lookup"><span data-stu-id="e2546-116">Procedures</span></span>](procedures.md)  
  
-   [<span data-ttu-id="e2546-117">문의 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="e2546-117">Batches of Statements</span></span>](batches-of-statements.md)  
  
-   [<span data-ttu-id="e2546-118">ISO 옵션의 효과</span><span class="sxs-lookup"><span data-stu-id="e2546-118">Effects of ISO Options</span></span>](effects-of-iso-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2546-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2546-119">See Also</span></span>  
 [<span data-ttu-id="e2546-120">ODBC&#41;&#40;쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="e2546-120">Executing Queries &#40;ODBC&#41;</span></span>](../executing-queries-odbc.md)  
  
  
