---
title: 추적 재생에 대한 고려 사항(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c2f030a0191596e40ef1ee9e2b0b2d4da34c773
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727603"
---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a><span data-ttu-id="b8810-102">추적 재생에 대한 고려 사항(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="b8810-102">Considerations for Replaying Traces (SQL Server Profiler)</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="b8810-103">는 다음과 같은 종류의 추적을 재생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-103">cannot replay the following kinds of traces:</span></span>  
  
-   <span data-ttu-id="b8810-104">트랜잭션 복제 및 기타 트랜잭션 로그 동작이 들어 있는 추적.</span><span class="sxs-lookup"><span data-stu-id="b8810-104">Traces that contain transactional replication and other transaction log activity.</span></span> <span data-ttu-id="b8810-105">이러한 이벤트는 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-105">These events are skipped.</span></span> <span data-ttu-id="b8810-106">다른 종류의 복제는 트랜잭션 로그를 표시하지 않으므로 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-106">Other types of replication do not mark the transaction log so they are not affected.</span></span>  
  
-   <span data-ttu-id="b8810-107">GUID(Globally Unique Identifier)가 관련된 작업을 포함한 추적.</span><span class="sxs-lookup"><span data-stu-id="b8810-107">Traces that contain operations that involve globally unique identifiers (GUID).</span></span> <span data-ttu-id="b8810-108">이런 이벤트는 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-108">These events will be skipped.</span></span>  
  
-   <span data-ttu-id="b8810-109">**bcp**유틸리티, BULK INSERT 문, READTEXT 문, WRITETEXT 문, UPDATETEXT 문 및 전체 텍스트 작업이 관련된 **text**, **ntext** 및 **image** 열에 대한 작업이 포함된 추적.</span><span class="sxs-lookup"><span data-stu-id="b8810-109">Traces that contain operations on **text**, **ntext**, and **image** columns involving the **bcp** utility, the BULK INSERT, READTEXT, WRITETEXT, and UPDATETEXT statements, and full-text operations.</span></span> <span data-ttu-id="b8810-110">이러한 이벤트는 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-110">These events are skipped.</span></span>  
  
-   <span data-ttu-id="b8810-111">**sp_getbindtoken** 및 **sp_bindsession** 시스템 저장 프로시저 등의 세션 바인딩이 포함된 추적.</span><span class="sxs-lookup"><span data-stu-id="b8810-111">Traces that contain session binding: **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span> <span data-ttu-id="b8810-112">이러한 이벤트는 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-112">These events are skipped.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8810-113">미리 구성된 재생 템플릿(**TSQL_Replay**)을 사용하지 않고 필요한 모든 데이터를 캡처하지 않으면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 는 추적을 재생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8810-113">If you do not use the preconfigured replay template (**TSQL_Replay**), and do not capture all required data, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] does not replay the trace.</span></span> <span data-ttu-id="b8810-114">자세한 내용은 [Replay Requirements](replay-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8810-114">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
 <span data-ttu-id="b8810-115">추적 재생에 필요한 권한에 대한 자세한 내용은 [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8810-115">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8810-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8810-116">See Also</span></span>  
 <span data-ttu-id="b8810-117">[bcp 유틸리티](../bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b8810-117">[bcp Utility](../bcp-utility.md) </span></span>  
 <span data-ttu-id="b8810-118">[SQL Server 이벤트 클래스 참조](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b8810-118">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="b8810-119">[sp_getbindtoken&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b8810-119">[sp_getbindtoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql) </span></span>  
 <span data-ttu-id="b8810-120">[sp_bindsession&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b8810-120">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 <span data-ttu-id="b8810-121">[BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b8810-121">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="b8810-122">[READTEXT&#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b8810-122">[READTEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/readtext-transact-sql) </span></span>  
 <span data-ttu-id="b8810-123">[WRITETEXT&#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b8810-123">[WRITETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/writetext-transact-sql) </span></span>  
 [<span data-ttu-id="b8810-124">UPDATETEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b8810-124">UPDATETEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/updatetext-transact-sql)  
  
  
