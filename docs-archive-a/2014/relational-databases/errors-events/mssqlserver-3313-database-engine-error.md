---
title: MSSQLSERVER_3313 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3313 (Database Engine error)
ms.assetid: a244227b-8553-42df-9435-034f906c4c74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 94de98c248713927790efb0d04c4e1358df30e2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650052"
---
# <a name="mssqlserver_3313"></a><span data-ttu-id="f2a6f-102">MSSQLSERVER_3313</span><span class="sxs-lookup"><span data-stu-id="f2a6f-102">MSSQLSERVER_3313</span></span>
    
## <a name="details"></a><span data-ttu-id="f2a6f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="f2a6f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2a6f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="f2a6f-104">Product Name</span></span>|<span data-ttu-id="f2a6f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f2a6f-105">SQL Server</span></span>|  
|<span data-ttu-id="f2a6f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="f2a6f-106">Event ID</span></span>|<span data-ttu-id="f2a6f-107">3313</span><span class="sxs-lookup"><span data-stu-id="f2a6f-107">3313</span></span>|  
|<span data-ttu-id="f2a6f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="f2a6f-108">Event Source</span></span>|<span data-ttu-id="f2a6f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f2a6f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f2a6f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="f2a6f-110">Component</span></span>|<span data-ttu-id="f2a6f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f2a6f-111">SQLEngine</span></span>|  
|<span data-ttu-id="f2a6f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="f2a6f-112">Symbolic Name</span></span>|<span data-ttu-id="f2a6f-113">ERR_LOG_RID1</span><span class="sxs-lookup"><span data-stu-id="f2a6f-113">ERR_LOG_RID1</span></span>|  
|<span data-ttu-id="f2a6f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="f2a6f-114">Message Text</span></span>|<span data-ttu-id="f2a6f-115">데이터베이스 '%.\*ls'에 로그된 작업을 다시 실행하는 중 로그 레코드 ID %S_LSN에서 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-115">During redoing of a logged operation in database '%.\*ls', an error occurred at log record ID %S_LSN.</span></span> <span data-ttu-id="f2a6f-116">일반적으로 특정 실패는 Windows 이벤트 로그 서비스에서 이미 오류로 로그됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-116">Typically, the specific failure is previously logged as an error in the Windows Event Log service.</span></span> <span data-ttu-id="f2a6f-117">전체 백업에서 데이터베이스를 복원하거나 데이터베이스를 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-117">Restore the database from a full backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2a6f-118">설명</span><span class="sxs-lookup"><span data-stu-id="f2a6f-118">Explanation</span></span>  
 <span data-ttu-id="f2a6f-119">다시 실행 복구에 대한 롤업 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-119">This is a roll-up error for redo recovery.</span></span> <span data-ttu-id="f2a6f-120">이 오류가 발생하면 데이터베이스가 SUSPECT 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="f2a6f-121">주 파일 그룹(다른 파일 그룹도 해당될 수 있음)이 주의 대상이거나 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="f2a6f-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하는 동안에는 데이터베이스를 복구할 수 없으므로 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="f2a6f-123">문제를 해결하려면 사용자 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="f2a6f-124">**tempdb**에 대해 이 오류가 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2a6f-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="f2a6f-125">User Action</span></span>  
 <span data-ttu-id="f2a6f-126">이 오류는 서버 인스턴스를 시작하거나 데이터베이스를 복구하려는 지정된 시도 중에 시스템에 존재하는 일시적인 상태에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="f2a6f-127">또한 데이터베이스를 시작할 때마다 발생하는 영구적인 오류로 인해 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="f2a6f-128">오류의 원인을 확인하려면 Windows 이벤트 로그에서 구체적인 오류를 나타내는 이전 오류를 조사하십시오.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="f2a6f-129">이 오류 상태가 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 일반적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **LOG** 폴더에 3개의 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-129">Note that when this error condition is encountered, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] typically generates three files in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **LOG** folder.</span></span> <span data-ttu-id="f2a6f-130">SQLDump*nnnn*.txt 파일에는 트랜잭션에 대한 세부 정보와 문제가 발생한 페이지를 비롯하여 오류와 관련된 고급 진단 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-130">The SQLDump*nnnn*.txt file contains advanced diagnostic information relating to the failures, including the details about the transaction and the page that encountered the problem.</span></span> <span data-ttu-id="f2a6f-131">이 정보는 일반적으로 제품 지원 팀에서 오류 원인을 분석하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-131">This information is typically used by the Product Support team to analyze the reason for the failure.</span></span>  
  
 <span data-ttu-id="f2a6f-132">3313 오류가 발생한 원인에 대한 자세한 내용을 보려면 Windows 이벤트 로그에서 해당 문제를 가리키는 이전 오류를 조사하세요.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-132">For information about the cause of this occurrence of error 3313, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="f2a6f-133">적절한 사용자 동작은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류가 일시적인 상태에 의해 발생했는지 영구적인 문제에 의해 발생했는지를 나타내는 Windows 이벤트 로그의 정보에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-133">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="f2a6f-134">3313 오류 문제를 해결하기 위한 사용자 동작에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2a6f-134">For information about the user actions for troubleshooting error 3313, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a6f-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2a6f-135">See Also</span></span>  
 <span data-ttu-id="f2a6f-136">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2a6f-136">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="f2a6f-137">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f2a6f-137">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="f2a6f-138">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="f2a6f-138">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="f2a6f-139">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="f2a6f-139">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="f2a6f-140">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f2a6f-140">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
