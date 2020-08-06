---
title: 고유하게 컴파일된 저장 프로시저 및 Execution Set 옵션 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 264a2b3ab1e6f3f0bda97bfe89a4438aa641577d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742071"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a><span data-ttu-id="15c1b-102">고유하게 컴파일된 저장 프로시저 및 Execution Set 옵션</span><span class="sxs-lookup"><span data-stu-id="15c1b-102">Natively Compiled Stored Procedures and Execution Set Options</span></span>
  <span data-ttu-id="15c1b-103">ATOMIC 블록에서 Session 옵션은 고정됩니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-103">Session options are fixed in atomic blocks.</span></span> <span data-ttu-id="15c1b-104">저장 프로시저 실행은 세션의 SET 옵션의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-104">A stored procedure's execution is not affected by a session's SET options.</span></span> <span data-ttu-id="15c1b-105">하지만 SET NOEXEC, SET SHOWPLAN_XML과 같은 일부 SET 옵션은 저장 프로시저(고유하게 컴파일된 저장 프로시저 포함)가 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-105">However, certain SET options, such as SET NOEXEC and SET SHOWPLAN_XML, cause stored procedures (including natively compiled stored procedures) to not execute.</span></span>  
  
 <span data-ttu-id="15c1b-106">STATISTICS 옵션을 사용하도록 설정한 상태에서 고유하게 컴파일된 저장 프로시저를 실행하면 프로시저에 대한 통계가 문별로 수집되지 않고 전체적으로 수집됩니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-106">When a natively compiled stored procedure is executed with any STATISTICS option turned on, statistics are gathered for the procedure as a whole and not per statement.</span></span> <span data-ttu-id="15c1b-107">자세한 내용은 [SET STATISTICS IO&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [STATISTICS PROFILE&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [STATISTICS TIME&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql) 및 [STATISTICS XML&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15c1b-107">For more information, see [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql), and [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql).</span></span> <span data-ttu-id="15c1b-108">고유하게 컴파일된 저장 프로시저의 문별 수준에 대한 실행 통계를 구하려면 저장 프로시저의 각 개별 쿼리 실행이 완료될 때 시작되는 sp_statement_completed 이벤트에 확장 이벤트 세션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-108">To obtain execution statistics on a per-statement level in natively compiled stored procedures, use an Extended Event session on the sp_statement_completed event, which starts when each individual query in a stored procedures execution completes.</span></span> <span data-ttu-id="15c1b-109">확장 이벤트 세션을 만드는 방법은 [CREATE EVENT SESSION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15c1b-109">For more information on creating Extended Event sessions, see [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).</span></span>  
  
 <span data-ttu-id="15c1b-110">`SHOWPLAN_XML`은 고유하게 컴파일된 저장 프로시저에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-110">`SHOWPLAN_XML` is supported for natively compiled stored procedures.</span></span> <span data-ttu-id="15c1b-111">`SHOWPLAN_ALL` 및 `SHOWPLAN_TEXT`는 고유하게 컴파일된 저장 프로시저에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-111">`SHOWPLAN_ALL` and `SHOWPLAN_TEXT` are not supported with natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="15c1b-112">`SET FMTONLY`는 고유하게 컴파일된 저장 프로시저에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15c1b-112">`SET FMTONLY` in not supported with natively compiled stored procedures.</span></span> <span data-ttu-id="15c1b-113">대신 [sp_describe_first_result_set&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql)를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="15c1b-113">Use [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c1b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15c1b-114">See Also</span></span>  
 [<span data-ttu-id="15c1b-115">고유하게 컴파일된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="15c1b-115">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
