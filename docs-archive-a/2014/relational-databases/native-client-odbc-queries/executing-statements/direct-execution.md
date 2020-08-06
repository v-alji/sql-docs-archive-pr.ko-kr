---
title: 직접 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: rothja
ms.author: jroth
ms.openlocfilehash: 29153f3e4e9265e87feb0e23ba9ae97118691e95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646408"
---
# <a name="direct-execution"></a><span data-ttu-id="12a26-102">직접 실행</span><span class="sxs-lookup"><span data-stu-id="12a26-102">Direct Execution</span></span>
  <span data-ttu-id="12a26-103">직접 실행은 가장 기본적인 문 실행 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-103">Direct execution is the most basic way to execute a statement.</span></span> <span data-ttu-id="12a26-104">응용 프로그램은 문을 포함 하는 문자열을 작성 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 하 고 **Sqlexecdirect** 함수를 사용 하 여 실행을 위해 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-104">An application builds a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submits it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="12a26-105">서버에서 문이 수신되면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 문을 실행 계획으로 컴파일한 다음 실행 계획을 즉시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-105">When the statement reaches the server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compiles it into an execution plan and then immediately runs the execution plan.</span></span>  
  
 <span data-ttu-id="12a26-106">직접 실행은 런타임에 문을 작성하고 실행하는 애플리케이션에 많이 사용되며, 한 번 실행되는 문에 가장 효율적인 실행 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-106">Direct execution is commonly used by applications that build and execute statements at run time and is the most efficient method for statements that will be executed a single time.</span></span> <span data-ttu-id="12a26-107">반면 실행할 때마다 SQL 문을 구문 분석하고 컴파일해야 하기 때문에 문을 여러 번 실행하는 경우 오버헤드가 증가한다는 점이 많은 데이터베이스에서 단점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-107">Its drawback with many databases is that the SQL statement must be parsed and compiled each time it is executed, which adds overhead if the statement is executed multiple times.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="12a26-108">에서는 다중 사용자 환경에서 자주 실행되는 문의 직접 실행 성능이 크게 향상되었으며, 자주 실행되는 SQL 문에 대한 매개 변수 표식과 SQLExecDirect를 함께 사용하여 준비된 실행의 효율성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-108">significantly improves the performance of direct execution of commonly executed statements in multiuser environments and using SQLExecDirect with parameter markers for commonly executed SQL statements can approach the efficiency of prepared execution.</span></span>  
  
 <span data-ttu-id="12a26-109">의 인스턴스에 연결 된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버는 [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) 을 사용 하 여 **SQLEXECDIRECT**에 지정 된 SQL 문 또는 일괄 처리를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-109">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) to transmit the SQL statement or batch specified on **SQLExecDirect**.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="12a26-110">에는 **sp_executesql** 실행 중인 SQL 문 또는 일괄 처리가 메모리에 이미 있는 실행 계획을 생성 한 문 또는 일괄 처리와 일치 하는지 빠르게 확인 하는 논리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-110">has logic to quickly determine if an SQL statement or batch executed with **sp_executesql** matches the statement or batch that generated an execution plan that already exists in memory.</span></span> <span data-ttu-id="12a26-111">일치하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 새 계획을 컴파일하는 대신 기존 계획을 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-111">If a match is made, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] simply reuses the existing plan rather than compile a new plan.</span></span> <span data-ttu-id="12a26-112">즉, 사용자가 많은 시스템에서 **Sqlexecdirect** 를 사용 하 여 실행 되는 일반적으로 실행 되는 SQL 문은 이전 버전의 저장 프로시저 에서만 사용할 수 있었던 대부분의 계획 재사용 혜택을 활용 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="12a26-112">This means that commonly executed SQL statements executed with **SQLExecDirect** in a system with many users will benefit from many of the plan-reuse benefits that were only available to stored procedures in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="12a26-113">실행 계획을 다시 사용하는 데 따른 이러한 이점은 여러 사용자가 동일한 SQL 문 또는 일괄 처리를 실행하는 경우에만 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-113">This benefit of reusing execution plans only works when several users are executing the same SQL statement or batch.</span></span> <span data-ttu-id="12a26-114">여러 클라이언트에서 실행되는 SQL 문에서 실행 계획의 다시 사용 가능성을 높이려면 다음 코딩 규칙을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="12a26-114">Follow these coding conventions to increase the probability that the SQL statements executed by different clients are similar enough to be able to reuse execution plans:</span></span>  
  
-   <span data-ttu-id="12a26-115">SQL 문에 데이터 상수를 포함하지 않습니다. 대신 프로그램 변수에 바인딩된 매개 변수 표식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-115">Do not include data constants in the SQL statements; instead use parameter markers bound to program variables.</span></span> <span data-ttu-id="12a26-116">자세한 내용은 [문 매개 변수 사용](../using-statement-parameters.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12a26-116">For more information, see [Using Statement Parameters](../using-statement-parameters.md).</span></span>  
  
-   <span data-ttu-id="12a26-117">정규화된 개체 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-117">Use fully qualified object names.</span></span> <span data-ttu-id="12a26-118">개체 이름이 정규화되어 있지 않으면 실행 계획이 다시 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-118">Execution plans are not reused if object names are not qualified.</span></span>  
  
-   <span data-ttu-id="12a26-119">애플리케이션 연결에 공통 연결 및 문 옵션을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-119">Have application connections as possible use a common set of connection and statement options.</span></span> <span data-ttu-id="12a26-120">하나의 옵션 집합(예: ANSI_NULLS)을 사용하는 연결에 대해 생성되는 실행 계획은 다른 옵션 집합이 추가로 사용된 연결에 다시 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-120">Execution plans generated for a connection with one set of options (such as ANSI_NULLS) are not reused for a connection having another set of options.</span></span> <span data-ttu-id="12a26-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자는 이러한 옵션에 대한 기본 설정이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-121">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider both have the same default settings for these options.</span></span>  
  
 <span data-ttu-id="12a26-122">**Sqlexecdirect** 를 사용 하 여 실행 된 모든 문이 이러한 규칙을 사용 하 여 코딩 되는 경우는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기회가 발생할 때 실행 계획을 재사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12a26-122">If all statements executed with **SQLExecDirect** are coded using these conventions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can reuse execution plans when the opportunity arises.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a26-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12a26-123">See Also</span></span>  
 [<span data-ttu-id="12a26-124">ODBC&#41;&#40;문을 실행 하는 중</span><span class="sxs-lookup"><span data-stu-id="12a26-124">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
