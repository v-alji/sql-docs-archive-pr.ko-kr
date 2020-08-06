---
title: MSSQLSERVER_3456 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f13316bdd3147bb0ad63c8d4a2fb18f1fce74006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732704"
---
# <a name="mssqlserver_3456"></a><span data-ttu-id="72b0f-102">MSSQLSERVER_3456</span><span class="sxs-lookup"><span data-stu-id="72b0f-102">MSSQLSERVER_3456</span></span>
    
## <a name="details"></a><span data-ttu-id="72b0f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="72b0f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72b0f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="72b0f-104">Product Name</span></span>|<span data-ttu-id="72b0f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="72b0f-105">SQL Server</span></span>|  
|<span data-ttu-id="72b0f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="72b0f-106">Event ID</span></span>|<span data-ttu-id="72b0f-107">3456</span><span class="sxs-lookup"><span data-stu-id="72b0f-107">3456</span></span>|  
|<span data-ttu-id="72b0f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="72b0f-108">Event Source</span></span>|<span data-ttu-id="72b0f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="72b0f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="72b0f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="72b0f-110">Component</span></span>|<span data-ttu-id="72b0f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="72b0f-111">SQLEngine</span></span>|  
|<span data-ttu-id="72b0f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="72b0f-112">Symbolic Name</span></span>|<span data-ttu-id="72b0f-113">REC_REDOLSNMISMATCH</span><span class="sxs-lookup"><span data-stu-id="72b0f-113">REC_REDOLSNMISMATCH</span></span>|  
|<span data-ttu-id="72b0f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="72b0f-114">Message Text</span></span>|<span data-ttu-id="72b0f-115">로그 레코드 %S_LSN을 다시 실행할 수 없습니다(트랜잭션 ID %S_XID, 페이지 %S_PGID, 데이터베이스 '%.\*ls'(데이터베이스 ID %d)).</span><span class="sxs-lookup"><span data-stu-id="72b0f-115">Could not redo log record %S_LSN, for transaction ID %S_XID, on page %S_PGID, database '%.\*ls' (database ID %d).</span></span> <span data-ttu-id="72b0f-116">페이지: LSN = %S_LSN, 유형 = %ld.</span><span class="sxs-lookup"><span data-stu-id="72b0f-116">Page: LSN = %S_LSN, type = %ld.</span></span> <span data-ttu-id="72b0f-117">로그: OpCode = %ld, 컨텍스트 %ld, PrevPageLSN: %S_LSN.</span><span class="sxs-lookup"><span data-stu-id="72b0f-117">Log: OpCode = %ld, context %ld, PrevPageLSN: %S_LSN.</span></span> <span data-ttu-id="72b0f-118">데이터베이스 백업에서 복원하거나 데이터베이스를 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="72b0f-118">Restore from a backup of the database, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="72b0f-119">설명</span><span class="sxs-lookup"><span data-stu-id="72b0f-119">Explanation</span></span>  
 <span data-ttu-id="72b0f-120">복원 작업에서 트랜잭션 로그를 다시 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-120">The restore operation was unable to redo the transaction log.</span></span> <span data-ttu-id="72b0f-121">이 오류가 발생하면 데이터베이스가 SUSPECT 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-121">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="72b0f-122">주 파일 그룹(다른 파일 그룹도 해당될 수 있음)이 주의 대상이거나 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-122">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="72b0f-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하는 동안에는 데이터베이스를 복구할 수 없으므로 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-123">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="72b0f-124">문제를 해결하려면 사용자 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-124">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="72b0f-125">**tempdb**에 대해 이 오류가 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-125">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="72b0f-126">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="72b0f-126">User Action</span></span>  
 <span data-ttu-id="72b0f-127">이 오류는 서버 인스턴스를 시작하거나 데이터베이스를 복구하려는 지정된 시도 중에 시스템에 존재하는 일시적인 상태에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-127">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="72b0f-128">또한 데이터베이스를 시작할 때마다 발생하는 영구적인 오류로 인해 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-128">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="72b0f-129">오류의 원인을 확인하려면 Windows 이벤트 로그에서 구체적인 오류를 나타내는 이전 오류를 조사하십시오.</span><span class="sxs-lookup"><span data-stu-id="72b0f-129">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="72b0f-130">3456 오류가 발생한 원인에 대한 자세한 내용을 보려면 Windows 이벤트 로그에서 해당 문제를 가리키는 이전 오류를 조사하세요.</span><span class="sxs-lookup"><span data-stu-id="72b0f-130">For information about the cause of this occurrence of error 3456, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="72b0f-131">적절한 사용자 동작은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류가 일시적인 상태에 의해 발생했는지 영구적인 문제에 의해 발생했는지를 나타내는 Windows 이벤트 로그의 정보에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="72b0f-131">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="72b0f-132">3456 오류 문제를 해결하기 위한 사용자 동작에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72b0f-132">For information about the user actions for troubleshooting error 3456, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b0f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72b0f-133">See Also</span></span>  
 <span data-ttu-id="72b0f-134">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="72b0f-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="72b0f-135">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="72b0f-135">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="72b0f-136">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="72b0f-136">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="72b0f-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="72b0f-137">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="72b0f-138">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="72b0f-138">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
