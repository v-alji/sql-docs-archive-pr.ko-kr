---
title: MSSQLSERVER_3314 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3314 (Database Engine error)
ms.assetid: f3a5ca6a-b502-4cab-b3b1-4bc753763fa9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff3b891b438f71d70f5dd62174eae2c5a07d29a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653903"
---
# <a name="mssqlserver_3314"></a><span data-ttu-id="a91c1-102">MSSQLSERVER_3314</span><span class="sxs-lookup"><span data-stu-id="a91c1-102">MSSQLSERVER_3314</span></span>
    
## <a name="details"></a><span data-ttu-id="a91c1-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="a91c1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a91c1-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a91c1-104">Product Name</span></span>|<span data-ttu-id="a91c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a91c1-105">SQL Server</span></span>|  
|<span data-ttu-id="a91c1-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a91c1-106">Event ID</span></span>|<span data-ttu-id="a91c1-107">3314</span><span class="sxs-lookup"><span data-stu-id="a91c1-107">3314</span></span>|  
|<span data-ttu-id="a91c1-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a91c1-108">Event Source</span></span>|<span data-ttu-id="a91c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a91c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a91c1-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a91c1-110">Component</span></span>|<span data-ttu-id="a91c1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a91c1-111">SQLEngine</span></span>|  
|<span data-ttu-id="a91c1-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a91c1-112">Symbolic Name</span></span>|<span data-ttu-id="a91c1-113">ERR_LOG_RID2</span><span class="sxs-lookup"><span data-stu-id="a91c1-113">ERR_LOG_RID2</span></span>|  
|<span data-ttu-id="a91c1-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a91c1-114">Message Text</span></span>|<span data-ttu-id="a91c1-115">데이터베이스 '%.\*ls'에 로그된 작업을 실행 취소하는 중 로그 레코드 %S_LSN에서 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-115">During undoing of a logged operation in database '%.\*ls', an error occurred at log record ID %S_LSN.</span></span> <span data-ttu-id="a91c1-116">일반적으로 특정 오류는 Windows 이벤트 로그 서비스에서 이미 오류로 로깅되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-116">Typically, the specific failure is logged previously as an error in the Windows Event Log service.</span></span> <span data-ttu-id="a91c1-117">백업에서 데이터베이스 또는 파일을 복원하거나 데이터베이스를 복구하십시오.</span><span class="sxs-lookup"><span data-stu-id="a91c1-117">Restore the database or file from a backup, or repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a91c1-118">설명</span><span class="sxs-lookup"><span data-stu-id="a91c1-118">Explanation</span></span>  
 <span data-ttu-id="a91c1-119">실행 취소 복구에 대한 롤업 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-119">This is a rollup error for undo recovery.</span></span> <span data-ttu-id="a91c1-120">이 오류가 발생하면 데이터베이스가 SUSPECT 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-120">This error has placed the database into the SUSPECT state.</span></span> <span data-ttu-id="a91c1-121">주 파일 그룹(다른 파일 그룹도 해당될 수 있음)이 주의 대상이거나 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-121">The primary filegroup, and possibly other filegroups, are suspect and may be damaged.</span></span> <span data-ttu-id="a91c1-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하는 동안에는 데이터베이스를 복구할 수 없으므로 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-122">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is therefore unavailable.</span></span> <span data-ttu-id="a91c1-123">문제를 해결하려면 사용자 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-123">User action is required to resolve the problem.</span></span>  
  
 <span data-ttu-id="a91c1-124">**tempdb**에 대해 이 오류가 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-124">Note that if this error occurs for **tempdb**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a91c1-125">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a91c1-125">User Action</span></span>  
 <span data-ttu-id="a91c1-126">이 오류는 서버 인스턴스를 시작하거나 데이터베이스를 복구하려는 지정된 시도 중에 시스템에 존재하는 일시적인 상태에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-126">This error can be caused by a transient condition that existed on the system during a given attempt to start up the server instance or to recover a database.</span></span> <span data-ttu-id="a91c1-127">또한 데이터베이스를 시작할 때마다 발생하는 영구적인 오류로 인해 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-127">This error can also be caused by a permanent failure that occurs every time that you attempt to start the database.</span></span> <span data-ttu-id="a91c1-128">오류의 원인을 확인하려면 Windows 이벤트 로그에서 구체적인 오류를 나타내는 이전 오류를 조사하십시오.</span><span class="sxs-lookup"><span data-stu-id="a91c1-128">For information about the cause, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span>  
  
 <span data-ttu-id="a91c1-129">3314 오류가 발생한 원인에 대한 자세한 내용을 보려면 Windows 이벤트 로그에서 해당 문제를 가리키는 이전 오류를 조사하십시오.</span><span class="sxs-lookup"><span data-stu-id="a91c1-129">For information about the cause of this occurrence of error 3314, examine the Windows Event Log for a previous error that indicates the specific failure.</span></span> <span data-ttu-id="a91c1-130">적절한 사용자 동작은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류가 일시적인 상태에 의해 발생했는지 영구적인 문제에 의해 발생했는지를 나타내는 Windows 이벤트 로그의 정보에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a91c1-130">The appropriate user action depends on whether the information in the Windows Event Log indicates that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error was caused by a transient condition or a permanent failure.</span></span> <span data-ttu-id="a91c1-131">3314 오류 문제를 해결하기 위한 사용자 동작에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a91c1-131">For information about the user actions for troubleshooting error 3314, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91c1-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a91c1-132">See Also</span></span>  
 <span data-ttu-id="a91c1-133">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a91c1-133">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="a91c1-134">[DBCC CHECKDB &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a91c1-134">[DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) </span></span>  
 <span data-ttu-id="a91c1-135">[전체 데이터베이스 복원&#40;단순 복구 모델&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a91c1-135">[Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="a91c1-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span><span class="sxs-lookup"><span data-stu-id="a91c1-136">[MSSQLSERVER_824](mssqlserver-824-database-engine-error.md) </span></span>  
 [<span data-ttu-id="a91c1-137">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a91c1-137">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
