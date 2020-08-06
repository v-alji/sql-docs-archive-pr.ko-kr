---
title: 파일에 추적 결과 저장 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 644fc812bbb4863c336ff2f53f5b2d67ee0a4d5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646836"
---
# <a name="save-trace-results-to-a-file"></a><span data-ttu-id="73998-102">파일에 추적 결과 저장</span><span class="sxs-lookup"><span data-stu-id="73998-102">Save Trace Results to a File</span></span>
  <span data-ttu-id="73998-103">추적 결과를 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73998-103">You can save trace results to a file.</span></span> <span data-ttu-id="73998-104">추적 파일은 추적 결과가 기록된 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="73998-104">A trace file is a file where the trace results are written.</span></span> <span data-ttu-id="73998-105">추적 파일은 로컬 디렉터리(예: C:\\*foldername*\\*filename.trc*) 또는 네트워크 디렉터리(예: \\\computername\sharename\filename.trc)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73998-105">A trace file can be located either in a local directory (such as C:\\*foldername*\\*filename.trc*) or a network directory (such as \\\computername\sharename\filename.trc).</span></span>  
  
 <span data-ttu-id="73998-106">추적 파일을 사용하여 다음 작업을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73998-106">You can use the trace files to do the following:</span></span>  
  
-   <span data-ttu-id="73998-107">추적 재생</span><span class="sxs-lookup"><span data-stu-id="73998-107">Replay traces</span></span>  
  
-   <span data-ttu-id="73998-108">감사 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73998-108">Audit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="73998-109">성능 분석 관리</span><span class="sxs-lookup"><span data-stu-id="73998-109">Conduct performance analysis</span></span>  
  
-   <span data-ttu-id="73998-110">추적 이벤트와 성능 카운터의 상관 관계 지정으로 문제 감지 기능 향상</span><span class="sxs-lookup"><span data-stu-id="73998-110">Correlate trace events with performance counters to enhance problem detection</span></span>  
  
-   <span data-ttu-id="73998-111">데이터베이스 엔진 튜닝 관리자 분석 수행</span><span class="sxs-lookup"><span data-stu-id="73998-111">Perform Database Engine Tuning Advisor analysis</span></span>  
  
-   <span data-ttu-id="73998-112">쿼리 최적화 수행</span><span class="sxs-lookup"><span data-stu-id="73998-112">Carry out query optimization</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="73998-113">**@tracefile**저장 프로시저 **sp_trace_create**의 인수에 경로 및 파일 이름이 지정 되 면 추적 결과를 파일에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="73998-113">saves trace results to a file when a path and file name are specified for the **@tracefile** argument of the stored procedure **sp_trace_create**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73998-114">추적 파일을 저장하기 위한 경로가 **sp_trace_create** 저장 프로시저에 지정되는 경우 서버에서 해당 디렉터리에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73998-114">If a path is specified to the **sp_trace_create** stored procedure for saving the trace file, the directory must be accessible to the server.</span></span> <span data-ttu-id="73998-115">또한 로컬 디렉터리가 **sp_trace_create**에 지정되는 경우 이는 서버 컴퓨터의 로컬 디렉터리라는 점을 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="73998-115">Also be aware that if a local directory is specified to **sp_trace_create**, it is a local directory on the server computer.</span></span>  
  
 <span data-ttu-id="73998-116">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하면 추적 결과를 파일 또는 테이블에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73998-116">If [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is used, it allows you to save trace results to a file or to a table.</span></span> <span data-ttu-id="73998-117">추적 결과를 테이블에 저장하면 파일에 저장할 때와 똑같이 액세스할 수 있을 뿐 아니라 테이블을 쿼리하여 특정 이벤트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73998-117">Saving trace results to a table allows the same access as saving the trace to a file plus you can query the table to search for specific events.</span></span>  
  
 <span data-ttu-id="73998-118">추적 결과를 저장하는 방법은 [테이블에 추적 결과 저장&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) 및 [파일에 추적 결과 저장&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73998-118">For more information about saving trace results, see [Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) and [Save Trace Results to a File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73998-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73998-119">See Also</span></span>  
 <span data-ttu-id="73998-120">[sp_trace_create&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73998-120">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="73998-121">[추적 만들기&#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="73998-121">[Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md) </span></span>  
 [<span data-ttu-id="73998-122">추적 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="73998-122">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
