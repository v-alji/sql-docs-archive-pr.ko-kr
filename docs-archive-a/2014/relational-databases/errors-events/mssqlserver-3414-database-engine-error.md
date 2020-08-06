---
title: MSSQLSERVER_3414 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aecaf2a920552b8ea66804600fa8bd4168175e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653896"
---
# <a name="mssqlserver_3414"></a><span data-ttu-id="5e6e2-102">MSSQLSERVER_3414</span><span class="sxs-lookup"><span data-stu-id="5e6e2-102">MSSQLSERVER_3414</span></span>
    
## <a name="details"></a><span data-ttu-id="5e6e2-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5e6e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e6e2-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5e6e2-104">Product Name</span></span>|<span data-ttu-id="5e6e2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5e6e2-105">SQL Server</span></span>|  
|<span data-ttu-id="5e6e2-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5e6e2-106">Event ID</span></span>|<span data-ttu-id="5e6e2-107">3414</span><span class="sxs-lookup"><span data-stu-id="5e6e2-107">3414</span></span>|  
|<span data-ttu-id="5e6e2-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5e6e2-108">Event Source</span></span>|<span data-ttu-id="5e6e2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5e6e2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5e6e2-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5e6e2-110">Component</span></span>|<span data-ttu-id="5e6e2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5e6e2-111">SQLEngine</span></span>|  
|<span data-ttu-id="5e6e2-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5e6e2-112">Symbolic Name</span></span>|<span data-ttu-id="5e6e2-113">REC_GIVEUP</span><span class="sxs-lookup"><span data-stu-id="5e6e2-113">REC_GIVEUP</span></span>|  
|<span data-ttu-id="5e6e2-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5e6e2-114">Message Text</span></span>|<span data-ttu-id="5e6e2-115">복구하는 동안 오류가 발생하여 데이터베이스 '%.\*ls'(데이터베이스 ID %d)을(를) 다시 시작하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-115">An error occurred during recovery, preventing the database '%.\*ls' (database ID %d) from restarting.</span></span> <span data-ttu-id="5e6e2-116">복구 오류를 진단하여 수정하거나 양호한 백업에서 복원하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-116">Diagnose the recovery errors and fix them, or restore from a known good backup.</span></span> <span data-ttu-id="5e6e2-117">오류를 수정할 수 없거나 예상할 수 없는 경우 기술 지원 서비스에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-117">If errors are not corrected or expected, contact Technical Support.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5e6e2-118">설명</span><span class="sxs-lookup"><span data-stu-id="5e6e2-118">Explanation</span></span>  
 <span data-ttu-id="5e6e2-119">지정된 데이터베이스가 복구되었으나 복구 중 오류가 발생하여 시작에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-119">The specified database was recovered, but failed to start, because errors occurred during recovery.</span></span> <span data-ttu-id="5e6e2-120">이 오류가 발생하면 데이터베이스가 SUSPECT 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="5e6e2-121">주 파일 그룹(다른 파일 그룹도 해당될 수 있음)이 주의 대상이거나 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="5e6e2-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하는 동안에는 데이터베이스를 복구할 수 없으므로 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="5e6e2-123">문제를 해결하려면 사용자 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="5e6e2-124">**tempdb**에 대해 이 오류가 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5e6e2-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5e6e2-125">User Action</span></span>  
 <span data-ttu-id="5e6e2-126">이 오류는 서버 인스턴스를 시작하거나 데이터베이스를 복구하려는 지정된 시도 중에 시스템에 존재하는 일시적인 상태에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="5e6e2-127">또한 데이터베이스를 시작할 때마다 발생하는 영구적인 오류로 인해 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="5e6e2-128">오류의 원인을 확인하려면 Windows 이벤트 로그에서 구체적인 오류를 나타내는 이전 오류를 조사하십시오.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="5e6e2-129">3414 오류가 발생한 원인에 대한 자세한 내용을 보려면 Windows 이벤트 로그에서 해당 문제를 가리키는 이전 오류를 조사하세요.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-129">For information about the cause of this occurrence of error 3414, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="5e6e2-130">적절한 사용자 동작은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류가 일시적인 상태에 의해 발생했는지 영구적인 문제에 의해 발생했는지를 나타내는 Windows 이벤트 로그의 정보에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-130">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="5e6e2-131">3414 오류 문제를 해결하기 위한 사용자 동작에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e6e2-131">For information about the user actions for troubleshooting error 3414, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e6e2-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e6e2-132">See Also</span></span>  
 <span data-ttu-id="5e6e2-133">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e6e2-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="5e6e2-134">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e6e2-134">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="5e6e2-135">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="5e6e2-135">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="5e6e2-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="5e6e2-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="5e6e2-137">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5e6e2-137">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
