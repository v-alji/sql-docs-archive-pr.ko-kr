---
title: 추적 삭제(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], deleting
- removing traces
- deleting traces
ms.assetid: a5502814-b281-42dd-b885-5c9368025ae6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b3551cff36ef6e2c2e9cc6a4d9b7056ae44cb950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651602"
---
# <a name="delete-a-trace-transact-sql"></a><span data-ttu-id="2967d-102">추적 삭제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2967d-102">Delete a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="2967d-103">이 항목에서는 저장 프로시저를 사용하여 추적을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2967d-103">This topic describes how to use stored procedures to delete a trace.</span></span>  
  
 <span data-ttu-id="2967d-104">추적 저장 프로시저 사용에 대한 예는 [추적 만들기&#40;Transact-SQL&#41;](create-a-trace-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2967d-104">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](create-a-trace-transact-sql.md).</span></span>  
  
### <a name="to-delete-a-trace"></a><span data-ttu-id="2967d-105">추적을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="2967d-105">To delete a trace</span></span>  
  
1.  <span data-ttu-id="2967d-106">**@status = 0**을 지정해서 **sp_trace_setstatus**를 실행하여 추적을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="2967d-106">Execute **sp_trace_setstatus** by specifying **@status = 0** to stop the trace.</span></span>  
  
2.  <span data-ttu-id="2967d-107">**@status = 2**를 지정해서 **sp_trace_setstatus**를 실행하여 추적을 닫고 서버에서 추적 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2967d-107">Execute **sp_trace_setstatus** by specifying **@status = 2** to close the trace and delete its information from the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2967d-108">추적은 먼저 중지한 후 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2967d-108">A trace must be stopped first before it can be closed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2967d-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2967d-109">See Also</span></span>  
 <span data-ttu-id="2967d-110">[sp_trace_setstatus&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2967d-110">[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql) </span></span>  
 <span data-ttu-id="2967d-111">[시스템 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2967d-111">[System Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="2967d-112">SQL Server Profiler 저장 프로시저&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2967d-112">SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
