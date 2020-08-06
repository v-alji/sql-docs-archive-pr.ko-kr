---
title: SQL Server 프로파일러 실행에 필요한 권한 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], permissions
- traces [SQL Server], replaying
- replaying traces
- SQL Server Profiler, permissions
- security [SQL Server], SQL Server Profiler
ms.assetid: 5c580a87-88ae-4314-8fe1-54ade83f227f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e73ffe2e127299db9a9e37e48f089aab2cccca52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737281"
---
# <a name="permissions-required-to-run-sql-server-profiler"></a><span data-ttu-id="0fa17-102">SQL Server 프로파일러 실행에 필요한 권한</span><span class="sxs-lookup"><span data-stu-id="0fa17-102">Permissions Required to Run SQL Server Profiler</span></span>
  <span data-ttu-id="0fa17-103">기본적으로 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 를 실행하려면 추적 작성에 사용된 Transact-SQL 저장 프로시저와 같은 동일한 사용자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-103">By default, running [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] requires the same user permissions as the Transact-SQL stored procedures that are used to create traces.</span></span> <span data-ttu-id="0fa17-104">[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]를 실행하려면 사용자에게 ALTER TRACE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-104">To run [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], users must be granted the ALTER TRACE permission.</span></span> <span data-ttu-id="0fa17-105">자세한 내용은 [GRANT 서버 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0fa17-105">For more information, see [GRANT Server Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0fa17-106">SHOWPLAN, ALTER TRACE 또는 VIEW SERVER STATE 권한이 있는 사용자는 실행 계획 출력에 캡처된 쿼리를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-106">Users who have the SHOWPLAN, the ALTER TRACE, or the VIEW SERVER STATE permission can view queries that are captured in Showplan output.</span></span> <span data-ttu-id="0fa17-107">이러한 쿼리에는 암호 같은 중요한 정보가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-107">These queries may contain sensitive information such as passwords.</span></span> <span data-ttu-id="0fa17-108">따라서 db_owner 고정 데이터베이스 역할의 멤버나 sysadmin 고정 서버 역할의 멤버 같이 중요한 정보를 볼 지위에 있는 사용자에게만 이러한 권한을 부여하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-108">Therefore, we recommend that you only grant these permissions to users who are authorized to view sensitive information, such as members of the db_owner fixed database role, or members of the sysadmin fixed server role.</span></span> <span data-ttu-id="0fa17-109">또한 실행 계획 파일을 저장하거나 실행 계획 관련 이벤트가 포함된 파일을 추적할 때는 NTFS 파일 시스템이 적용된 위치만 사용하고 중요한 정보를 볼 지위에 있는 사용자에게만 해당 위치에 대한 액세스 권한을 부여하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-109">Additionally, we recommend that you only save Showplan files or trace files that contain Showplan-related events to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view sensitive information.</span></span>

## <a name="permissions-used-to-replay-traces"></a><span data-ttu-id="0fa17-110">추적 재생에 사용되는 권한</span><span class="sxs-lookup"><span data-stu-id="0fa17-110">Permissions Used to Replay Traces</span></span>
 <span data-ttu-id="0fa17-111">추적을 재생할 때도 추적을 재생하는 사용자에게 ALTER TRACE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-111">Replaying traces also requires that the user who is replaying the trace have the ALTER TRACE permission.</span></span>

 <span data-ttu-id="0fa17-112">그러나 추적을 재생하는 동안 재생 중인 추적에 로그인 감사 이벤트가 발생하는 경우 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 에서 EXECUTE AS 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-112">However, during replay, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] uses the EXECUTE AS command if an Audit Login event is encountered in the trace that is being replayed.</span></span> [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0fa17-113">에서는 EXECUTE AS 명령을 사용하여 로그인 이벤트와 연관된 사용자를 가장합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-113">uses the EXECUTE AS command to impersonate the user who is associated with the login event.</span></span>

 <span data-ttu-id="0fa17-114">[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 에서 재생 중인 추적에 로그인 이벤트가 발생하는 경우 다음 권한 검사가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-114">If [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] encounters a login event in a trace that is being replayed, the following permission checks are performed:</span></span>

1.  <span data-ttu-id="0fa17-115">사용자1(ALTER TRACE 권한 보유)이 추적 재생을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-115">User1, who has the ALTER TRACE permission, starts replaying a trace.</span></span>

2.  <span data-ttu-id="0fa17-116">사용자2에 대한 로그인 이벤트가 재생된 추적에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-116">A login event for User2 is encountered in the replayed trace.</span></span>

3.  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="0fa17-117">에서 EXECUTE AS 명령을 사용하여 사용자2를 가장합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-117">uses the EXECUTE AS command to impersonate User2.</span></span>

4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0fa17-118">에서 사용자2에 대한 인증을 시도하고 그 결과에 따라 다음 중 하나가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-118">attempts to authenticate User2, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="0fa17-119">사용자2가 인증 받지 못한 경우 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 는 오류를 반환하고 사용자1로 추적 재생을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-119">If User2 cannot be authenticated, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] returns an error, and continues replaying the trace as User1.</span></span>

    2.  <span data-ttu-id="0fa17-120">사용자2가 성공적으로 인증 받은 경우 사용자2로 추적 재생을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-120">If User2 is successfully authenticated, replaying the trace as User2 continues.</span></span>

5.  <span data-ttu-id="0fa17-121">대상 데이터베이스에 대해 사용자2에 대한 권한을 검사하고 그 결과에 따라 다음 중 하나가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-121">Permissions for User2 are checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="0fa17-122">사용자2가 대상 데이터베이스에 권한을 갖는 경우 가장이 성공적으로 수행되고 추적은 사용자2로 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-122">If User2 has permissions on the target database, impersonation has succeeded, and the trace is replayed as User2.</span></span>

    2.  <span data-ttu-id="0fa17-123">사용자2가 대상 데이터베이스에 권한을 갖지 않는 경우 서버에서 해당 데이터베이스의 게스트 사용자에 대해 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-123">If User2 does not have permissions on the target database, the server checks for a Guest user on that database.</span></span>

6.  <span data-ttu-id="0fa17-124">대상 데이터베이스에 대해 게스트 사용자의 존재를 검사하고 그 결과에 따라 다음 중 하나가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-124">Existence of a Guest user is checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="0fa17-125">게스트 계정이 있으면 추적이 게스트 계정으로 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-125">If a Guest account exists, the trace is replayed as the Guest account.</span></span>

    2.  <span data-ttu-id="0fa17-126">대상 데이터베이스에 게스트 계정이 없으면 오류가 반환되고 추적이 사용자1로 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-126">If no Guest account exists on the target database, an error is returned and the trace is replayed as User1.</span></span>

 <span data-ttu-id="0fa17-127">다음 다이어그램은 추적 재생 시 이러한 권한의 검사 프로세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fa17-127">The following diagram shows this process of checking permission when replaying traces:</span></span>

 <span data-ttu-id="0fa17-128">![SQL Server Profiler 추적 재생 권한](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler 추적 재생 권한")</span><span class="sxs-lookup"><span data-stu-id="0fa17-128">![SQL Server Profiler replay trace permissions](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler replay trace permissions")</span></span>

## <a name="see-also"></a><span data-ttu-id="0fa17-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fa17-129">See Also</span></span>
 <span data-ttu-id="0fa17-130">[Transact-sql&#41;재생 추적 &#40;SQL Server Profiler 저장 프로시저](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [Replay Traces](replay-traces.md) 는 추적 [&#40;](create-a-trace-sql-server-profiler.md) SQL Server Profiler&#41;추적 &#40;[재생](replay-a-trace-table-sql-server-profiler.md) SQL Server Profiler 추적 [파일&#41;재생](replay-a-trace-file-sql-server-profiler.md) &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="0fa17-130">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [Replay Traces](replay-traces.md) [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md) [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)</span></span>


